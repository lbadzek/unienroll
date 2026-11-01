
# UniEnroll – Entity Diagram

## Project
P02 – University Course Enrolment

## Description
UniEnroll is a university course enrolment system.
Students can enrol in available courses during an
enrolment window.

The system validates prerequisites, ECTS limits,
course capacity and waiting lists.

## Entity Relationship Diagram

```mermaid
erDiagram
    STUDENT ||--o{ ENROLMENT : has
    COURSE ||--o{ ENROLMENT : receives
    SEMESTER ||--o{ ENROLMENT : contains
    SEMESTER ||--o{ COURSE : offers
    COURSE ||--o{ COURSE_PREREQUISITE : requires
    COURSE ||--o{ COURSE_PREREQUISITE : prerequisite_of

    STUDENT {
        Long id PK
        String first_name
        String last_name
        String email UK
        String student_number UK
    }

    COURSE {
        Long id PK
        String code UK
        String name
        Integer ects
        Integer capacity
        Long semester_id FK
    }

    ENROLMENT {
        Long id PK
        Long student_id FK
        Long course_id FK
        Long semester_id FK
        String status
        LocalDateTime enrolled_at
        Integer waiting_position
        Integer final_grade
    }

    COURSE_PREREQUISITE {
        Long id PK
        Long course_id FK
        Long prerequisite_course_id FK
    }

    SEMESTER {
        Long id PK
        String name
        LocalDate start_date
        LocalDate end_date
        LocalDateTime enrolment_start
        LocalDateTime enrolment_end
        Integer max_ects
    }
```

## Relationships

- A student can have multiple enrolments.
- A course can have multiple enrolments.
- Each enrolment belongs to a student and a course.
- A semester contains multiple courses.
- Courses can require other courses as prerequisites.
- Enrolments can have ENROLLED, WAITING or
  WITHDRAWN status.

## Business Rules

1. Students cannot enrol outside the enrolment window.
2. Students cannot exceed the semester ECTS limit.
3. Students must satisfy course prerequisites.
4. Prerequisite relationships must not contain cycles.
5. Course capacity cannot be exceeded.
6. Students may join a waiting list when a course is full.
7. A scheduled job promotes eligible waiting students
   when places become available.
