# students-classrooms-courses-simoneaa
1er ejercicio de normalización de bases de datos

## Descripción

En este ejercicio se nos pedía normalizar los datos de una tabla proporcionada empleando las 3 Normas Formales. La tabla proporcionada era la siguiente:

## Normalización de la tabla

## Diagrama de Chen

```mermaid
---
title: Classroom ER Diagram
layout: elk
---
flowchart LR
    %% Entities
    classrooms(["classrooms"])
    courses(["courses"])
    students(["students"])

    %% Attributes
    id_classroom(((id_classroom)))
    classroom_description(((classroom_description)))
    id_course(((id_course)))
    course_name(((course_name)))
    classroom_id_c(((classroom_id)))
    id_student(((id_student)))
    first_name(((first_name)))
    last_name(((last_name)))
    classroom_id_s(((classroom_id)))

    %% Relationships
    classrooms -- "1" --> R1(( ))
    R1 -- "N" --> courses
    classrooms -- "1" --> R2(( ))
    R2 -- "N" --> students

    %% Attribute connections
    id_classroom --> classrooms
    classroom_description --> classrooms
    id_course --> courses
    course_name --> courses
    classroom_id_c --> courses
    id_student --> students
    first_name --> students
    last_name --> students
    classroom_id_s --> students
```

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
