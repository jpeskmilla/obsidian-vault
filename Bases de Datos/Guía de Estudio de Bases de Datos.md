# 1. Introducción a las Bases de Datos

- **¿Qué es una Base de Datos (BD)?** Una colección de datos interrelacionados, organizada para un acceso eficiente. Es una representación estructurada del mundo real que gestiona grandes cantidades de información de forma coherente.

- **¿Qué es un Sistema de Gestión de Bases de Datos (SGBD)?** Un software que actúa como interfaz entre el usuario y la base de datos, proporcionando un entorno seguro y eficiente para el almacenamiento y la manipulación de los datos.
## Componentes de un SGBD

|                             |                                                        |
| --------------------------- | ------------------------------------------------------ |
| **Componente**              | **Función Principal**                                  |
| Gestor de almacenamiento    | Organiza y gestiona los datos en el disco físico.      |
| Motor de base de datos      | Procesa y optimiza las consultas de los usuarios.      |
| Lenguajes de acceso a datos | Son los medios para interactuar con el SGBD (ej. SQL). |
| Diccionario de datos        | Almacena metadatos (datos sobre los datos).            |
| Subsistema de control       | Garantiza la ejecución segura de transacciones (ACID). |

# 2. Modelos de Datos

## Modelo Relacional

- Introducido por Edgar F. Codd en 1970.
    
- Representa los datos como **tablas** o relaciones.
    
- Se basa en la **álgebra relacional**, lo que garantiza la integridad de los datos.
    

## Modelos No Relacionales (NoSQL)

- **Apache Cassandra:** Base de datos distribuida de código abierto, ideal para alta disponibilidad y escalabilidad sin un punto único de fallo.
    
- **MongoDB:** Base de datos orientada a documentos (tipo JSON), muy flexible para datos no estructurados.
    

# 3. Modelado de Datos Conceptual

- **Modelo Entidad-Relación (MER):** Un modelo de alto nivel que describe los requisitos de datos con notación gráfica.
    

## Componentes del MER

- **Entidades:** Objetos del mundo real (rectángulos). Ej: `Estudiante`, `Curso`.
    
- **Atributos:** Propiedades de una entidad (óvalos).
    
    - **Clave:** Identifica de forma única (`ID_Estudiante`).
        
    - **Multivalorado:** Varios valores posibles.
        
    - **Derivado:** Se calcula a partir de otro atributo.
        
- **Relaciones:** Asociaciones entre entidades (rombos). Ej: `Matricula`.
    

## Cardinalidad y Participación

- **Cardinalidad:** Especifica el número de instancias de una entidad que se relacionan con otra.
    
    - `1:1` (Uno a uno)
        
    - `1:N` (Uno a muchos)
        
    - `N:1` (Muchos a uno)
        
    - `M:N` (Muchos a muchos)
        
- **Participación:** Describe si una entidad debe participar en una relación.
    
    - **Total:** Obligatoria (línea doble).
        
    - **Parcial:** Opcional (línea simple).
        

# 4. Transformación del MER al Modelo Relacional

- La transformación es un paso crucial para la implementación física.
    
- **Método de traducción estable:** Cada entidad y relación se convierte en una tabla separada.
    
- **Método de traducción mapeado:** Las entidades y relaciones se combinan para reducir el número de tablas y optimizar el esquema.
    

# 5. Lenguajes de Acceso a Datos

- **SQL (Structured Query Language):** El lenguaje estándar de la industria, de tipo declarativo.
    

## Tipos de Sentencias SQL

|   |   |   |
|---|---|---|
|**Tipo**|**Función**|**Ejemplos**|
|**DDL**|Define la estructura de la base de datos (esquemas y objetos).|`CREATE TABLE`, `ALTER TABLE`, `DROP VIEW`|
|**DML**|Consulta y manipula los datos de la base de datos.|`SELECT`, `INSERT`, `UPDATE`, `DELETE`|
|**DCL**|Controla los permisos de los usuarios.|`GRANT`, `REVOKE`|
|**TCL**|Controla el procesamiento de transacciones.|`COMMIT`, `ROLLBACK`, `SAVEPOINT`|

# 6. Consideraciones de Diseño

Un buen diseño debe ser **correcto** y **mínimo**.

- **Principio de Correctitud:** El esquema debe ser una representación fiel y completa de la realidad, sin ambigüedades.
    
- **Principio de Minimalidad (Normalización):** Cada elemento de la realidad debe aparecer solo una vez para evitar la redundancia y las anomalías de actualización.
    

## Tipos de Anomalías por Redundancia

|   |   |
|---|---|
|**Anomalía**|**Descripción**|
|**Inserción**|No se puede agregar un registro sin tener datos redundantes.|
|**Actualización**|Un cambio en un dato repetido requiere múltiples actualizaciones, lo que puede causar inconsistencia.|
|**Borrado**|Eliminar un registro puede borrar accidentalmente información importante.|