# students-classrooms-courses-simoneaa
1er ejercicio de normalización de bases de datos

## Descripción

En este ejercicio se nos pedía normalizar los datos de una tabla proporcionada empleando las 3 Normas Formales. La tabla proporcionada era la siguiente:

## Normalización de la tabla

## Diagrama de Chen

## Diagrama de patas de gallo

```mermaid
---
config:
  layout: elk
---
erDiagram
    CLASSROOMS ||--o{ STUDENTS : "1 to N"
    CLASSROOMS ||--o{ COURSES : "1 to N"
    
    CLASSROOMS {
        string id_classroom PK
        string classroom_description
    }
    
    STUDENTS {
        int id_student PK
        string first_name
        string last_name
        string classroom_id FK
    }
    
    COURSES {
        int id_course PK
        string course_name
        string classroom_id FK
    }
