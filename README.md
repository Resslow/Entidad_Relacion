# Documentación del Modelo Entidad-Relación

## Descripción General
Este modelo entidad-relación está diseñado para gestionar información relacionada con personas migrantes, sus características demográficas, nivel académico, y registros migratorios. La base de datos permite hacer un seguimiento de los movimientos migratorios, incluyendo países de origen y destino, así como características demográficas detalladas de las personas.

## Entidades Principales

### Tabla: persona
- **Descripción**: Almacena información detallada sobre cada individuo.
- **Atributos**:
  - `idpersona`: int - Identificador único para cada persona (Clave primaria)
  - `idpais_residencia`: int - País de residencia (Clave foránea a pais.idpais)
  - `idciudad_residencia`: int - Ciudad de residencia (Clave foránea a ciudad.idciudad)
  - `idciudad_nacimiento`: int - Ciudad de nacimiento (Clave foránea a ciudad.idciudad)
  - `idestadocivil`: int - Estado civil (Clave foránea a estadocivil.idestadocivil)
  - `idgenero`: int - Género (Clave foránea a genero.idgenero)
  - `idetnia`: int - Etnia (Clave foránea a etnia.idetnia)
  - `idgrupoedad`: int - Grupo de edad (Clave foránea a grupoedad.idgrupoedad)
  - `idnivelacademico`: int - Nivel académico (Clave foránea a nivelacademico.idnivelacademico)
  - `idarea_conocimiento`: int - Área de conocimiento (Clave foránea a areaconocimiento.idarea_conocimiento)
  - `idsubarea_conocimiento`: int - Subárea de conocimiento (Clave foránea a subareaconocimiento.idsubarea_conocimiento)
  - `edad`: int - Edad de la persona
  - `estatura`: int - Estatura en centímetros
  - `fecha_registro`: date - Fecha en que se registró a la persona

### Tabla: registromigratorio
- **Descripción**: Contiene información sobre los movimientos migratorios.
- **Atributos**:
  - `idregistro`: int - Identificador único del registro (Clave primaria)
  - `idpersona`: int - Persona relacionada con el registro migratorio
  - `fecha_emigracion`: date - Fecha en que ocurrió la emigración
  - `pais_origen`: int - País de origen (Clave foránea a pais.idpais)
  - `pais_destino`: int - País de destino (Clave foránea a pais.idpais)
  - `cantidad_personas`: int - Cantidad de personas incluidas en el registro
  - `idoficina`: int - Oficina donde se registró (Clave foránea a oficina_registro.idoficina)

### Tabla: pais
- **Descripción**: Catálogo de países.
- **Atributos**:
  - `idpais`: int - Identificador único del país (Clave primaria)
  - `nombre_pais`: varchar(100) - Nombre del país

### Tabla: ciudad
- **Descripción**: Catálogo de ciudades.
- **Atributos**:
  - `idciudad`: int - Identificador único de la ciudad (Clave primaria)
  - `nombre_ciudad`: varchar(255) - Nombre de la ciudad

### Tabla: estadocivil
- **Descripción**: Catálogo de estados civiles.
- **Atributos**:
  - `idestadocivil`: int - Identificador único del estado civil (Clave primaria)
  - `estado_civil`: varchar(50) - Descripción del estado civil

### Tabla: genero
- **Descripción**: Catálogo de géneros.
- **Atributos**:
  - `idgenero`: int - Identificador único del género (Clave primaria)
  - `genero`: varchar(50) - Descripción del género

### Tabla: etnia
- **Descripción**: Catálogo de etnias.
- **Atributos**:
  - `idetnia`: int - Identificador único de la etnia (Clave primaria)
  - `etnia`: varchar(50) - Descripción de la etnia

### Tabla: grupoedad
- **Descripción**: Catálogo de grupos de edad.
- **Atributos**:
  - `idgrupoedad`: int - Identificador único del grupo de edad (Clave primaria)
  - `grupo_edad`: varchar(50) - Descripción del grupo de edad

### Tabla: nivelacademico
- **Descripción**: Catálogo de niveles académicos.
- **Atributos**:
  - `idnivelacademico`: int - Identificador único del nivel académico (Clave primaria)
  - `nivel`: varchar(50) - Descripción del nivel académico

### Tabla: areaconocimiento
- **Descripción**: Catálogo de áreas de conocimiento.
- **Atributos**:
  - `idarea_conocimiento`: int - Identificador único del área (Clave primaria)
  - `area_conocimiento`: varchar(100) - Descripción del área de conocimiento

### Tabla: subareaconocimiento
- **Descripción**: Catálogo de subáreas de conocimiento.
- **Atributos**:
  - `idsubarea_conocimiento`: int - Identificador único de la subárea (Clave primaria)
  - `sub_area_conocimiento`: varchar(100) - Descripción de la subárea
  - `idarea_conocimiento`: int - Área de conocimiento a la que pertenece (Clave foránea a areaconocimiento.idarea_conocimiento)

### Tabla: oficina_registro
- **Descripción**: Catálogo de oficinas de registro migratorio.
- **Atributos**:
  - `idoficina`: int - Identificador único de la oficina (Clave primaria)
  - `nombre_oficina`: varchar(255) - Nombre de la oficina

## Relaciones

### Relaciones de la tabla persona
- **Relación con pais (idpais_residencia)**: Una persona reside en un país. Relación muchos a uno.
- **Relación con ciudad (idciudad_residencia)**: Una persona reside en una ciudad. Relación muchos a uno.
- **Relación con ciudad (idciudad_nacimiento)**: Una persona nació en una ciudad. Relación muchos a uno.
- **Relación con estadocivil**: Una persona tiene un estado civil. Relación muchos a uno.
- **Relación con genero**: Una persona tiene un género. Relación muchos a uno.
- **Relación con etnia**: Una persona pertenece a una etnia. Relación muchos a uno.
- **Relación con grupoedad**: Una persona pertenece a un grupo de edad. Relación muchos a uno.
- **Relación con nivelacademico**: Una persona tiene un nivel académico. Relación muchos a uno.
- **Relación con areaconocimiento**: Una persona está asociada a un área de conocimiento. Relación muchos a uno.
- **Relación con subareaconocimiento**: Una persona está asociada a una subárea de conocimiento. Relación muchos a uno.

### Relaciones de la tabla registromigratorio
- **Relación con pais (pais_origen)**: Un registro migratorio tiene un país de origen. Relación muchos a uno.
- **Relación con pais (pais_destino)**: Un registro migratorio tiene un país de destino. Relación muchos a uno.
- **Relación con oficina_registro**: Un registro migratorio se realiza en una oficina. Relación muchos a uno.
- **Relación implícita con persona**: Un registro migratorio está asociado a una persona mediante idpersona (aunque no hay una restricción formal de clave foránea en la estructura actual).

### Relación entre areaconocimiento y subareaconocimiento
- **Tipo**: One-to-Many (Un área de conocimiento puede tener múltiples subáreas)
- **Descripción**: Una subárea pertenece a un área de conocimiento específica.
- **Implementación**: Clave foránea idarea_conocimiento en la tabla subareaconocimiento.

## Diagrama Conceptual del Modelo Entidad-Relación

```
                         +-------------------+
                         |      persona      |
                         +-------------------+
                         | PK: idpersona     |
                         | FK: múltiples     |
                         +--------+----------+
                                  |
                                  | tiene
                                  |
               +------------------v----------------+
               |                                   |
    +----------+----------+            +-----------v----------+
    | registromigratorio  |            |    Tablas catálogo   |
    +---------------------+            +----------------------+
    | PK: idregistro      |            | - pais               |
    | FK: múltiples       |            | - ciudad             |
    +---------------------+            | - estadocivil        |
                                       | - genero             |
                                       | - etnia              |
                                       | - grupoedad          |
                                       | - nivelacademico     |
                                       | - areaconocimiento   |
                                       | - subareaconocimiento|
                                       | - oficina_registro   |
                                       +----------------------+
