# students-classrooms-courses-simoneaa
1er ejercicio de normalización de bases de datos

## Descripción

En este ejercicio se nos pedía normalizar los datos de una tabla proporcionada empleando las 3 Normas Formales. La tabla proporcionada era la siguiente:

<img src="/img1.jpg">

## Normalización de la tabla

Empleando Google Sheets, dividí la tabla proporcionada en tres diferentes, con "classrooms" siendo la principal y conteniendo "students" y "courses". La clave primaria "id_classroom" es la clave foránea que relaciona las otras dos tablas con la principal y entre ellas.

<img src="/img2.jpg">

## Diagrama de Chen

```mermaid
---
layout: elk
---
flowchart LR
    %% Entities (square shapes)
    classrooms["classrooms"]
    courses["courses"]
    students["students"]

    %% Attributes (small ovals)
    id_classroom(("id_classroom"))
    classroom_description(("classroom_description"))
    id_course(("id_course"))
    course_name(("course_name"))
    classroom_id_c(("classroom_id"))
    id_student(("id_student"))
    first_name(("first_name"))
    last_name(("last_name"))
    classroom_id_s(("classroom_id"))

    %% Relationships
    classrooms -- "1" --> R1((has))
    R1 -- "N" --> courses
    classrooms -- "1" --> R2((has))
    R2 -- "N" --> students

    %% Attribute links
    id_classroom --> classrooms
    classroom_description --> classrooms
    id_course --> courses
    course_name --> courses
    classroom_id_c --> courses
    id_student --> students
    first_name --> students
    last_name --> students
    classroom_id_s --> students

    %% Class definitions (monochrome scheme)
    classDef entity fill:#f5f5f5,stroke:#333,stroke-width:2px,color:#000,font-size:16px,font-weight:bold;
    classDef attribute fill:#fff,stroke:#333,stroke-width:1px,color:#000,font-size:12px;

    %% Apply classes
    class classrooms,courses,students entity;
    class id_classroom,classroom_description,id_course,course_name,classroom_id_c,id_student,first_name,last_name,classroom_id_s attribute;
```

<img src="/students-classrooms-courses-chen.jpg">

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
```

<img src="/students-classrooms-courses-gallo.jpg">
