# HUDA ACADEMY

A learning management and online assessment system for academic education.

## Features

- Admin adds courses, teachers, and students and assigns them courses.
- Teachers create course content, announcements, assignments, quizzes, take attendance, etc. Teachers can see the details and analysis of the assessments.
- Students can enroll in the courses using the access key, see the course content of the enrolled courses, participate in assessments, and see their results in detail.
- Discussion section for both teachers and students.

## Entity-Relationship Diagram (ERD)

### Entities

```
┌───────────────────────┐      ┌───────────────────────┐      ┌───────────────────────┐
│   main_assignment     │      │ attendance_attendance │      │   main_submission     │
├───────────────────────┤      ├───────────────────────┤      ├───────────────────────┤
│ assignment_id (PK)    │      │ attendance_id (PK)    │      │ submission_id (PK)    │
│ take (VARCHAR(255))   │      │ date (DATE)           │      │ file (VARCHAR(100))   │
│ description (LONGTEXT)│      │ status (TINYINT(1))   │      │ datetime (DATETIME)   │
│ datetime (DATETIME)   │      │ console_ID (DATETIME) │      │ make (DECIMAL(4,2))   │
│ deadline (DATETIME)   │      │ subdivid_at (DATETIME)│      │ status (VARCHAR(100)) │
│ file (VARCHAR(100))   │      │ course_id (INT)       │      │ assignment_id (INT)   │
│ make (DECIMAL(4,2))   │      │ subdivid_id (INT)     │      │ subdivid_id (INT)     │
│ course_code_id (INT)  │      └───────────────────────┘      └───────────────────────┘
└───────────────────────┘
            │                               │                              │
            │                               │                              │
            ▼                               ▼                              ▼
┌───────────────────────┐      ┌───────────────────────┐      ┌───────────────────────┐
│     main_student      │      │ student_discussion    │      │       data_data       │
├───────────────────────┤      ├───────────────────────┤      ├───────────────────────┤
│ student_id (PK)       │      │ discussion_id (PK)    │      │ data_id (PK)          │
│ number (VARCHAR(100)) │      │ content (LONGTEXT)    │      │ take (VARCHAR(100))   │
│ name (VARCHAR(100))   │      │ sent_at (DATETIME)    │      │ description (LONGTEXT)│
│ password VARCHAR (255)│      │ course_id (INT)       │      │ start (DATETIME)      │
│ role (VARCHAR(100))   │      │ sent_by_id (INT)      │      │ end (DATETIME)        │
│ photo (VARCHAR(100))  │      └───────────────────────┘      │ console_url (DATETIME)│
│ department_id (INT)   │                                     │ updated_at (DATETIME) │
└───────────────────────┘                                     │ publish_status        │
    ▲                                                         │ started (TINYINT(1))  │
    │                                                         │ course_id (INT)       │
    │                                                         └───────────────────────┘
    │                                                                   ▲
    │                                                                   │
    │                                                                   │
┌───────────────────────┐      ┌───────────────────────┐      ┌───────────────────────┐
│  main_announcement    │      │    main_material      │      │     main_faculty      │
├───────────────────────┤      ├───────────────────────┤      ├───────────────────────┤
│ announcement_id (PK)  │      │ material_id (PK)      │      │ faculty_id (PK)       │
│ take (VARCHAR(255))   │      │ take (VARCHAR(255))   │      │ name (VARCHAR(100))   │
│ description (LONGTEXT)│      │ description (LONGTEXT)│      │ email (VARCHAR(100))  │
│ datetime (DATETIME)   │      │ datetime (DATETIME)   │      │ password VARCHAR(255) │
│ course_code_id (INT)  │      │ file (VARCHAR(100))   │      │ role (VARCHAR(100))   │
└───────────────────────┘      │ course_code_id (INT)  │      │ photo (VARCHAR(100))  │
                               └───────────────────────┘      │ department_id (INT)   │
                                                              └───────────────────────┘
                ▲                          ▲                          ▲
                │                          │                          │
                │                          │                          │
                └──────────────────────────┴──────────────────────────┘
```

### Relationships Explained with Arrows

- `main_assignment` → `main_submission`: Assignments are linked to submissions.
- `main_student` → `main_submission`: Students submit assignments.
- `main_faculty` → `discussion_facultydiscussion`: Faculty participate in discussions.
- `main_student` → `discussion_studentdiscussion`: Students participate in discussions.
- `main_announcement` and `main_material` → `main_course`: Announcements and materials are tied to courses.
- `attendance_attendance` → `main_course`: Attendance is linked to courses.
- `data_data` → `main_course`: Data is associated with courses.

## Tech Stack

1. Django 4.0.4
2. Bootstrap 5.0.2
3. jQuery 3.6.0
4. Chart.js v3.9.1
5. Animate.css 4.1.1

## Run Locally

1. Clone the project

```bash
git clone <repository-url>
```

2. Go to the project directory

3. install virtual environment and activate it

```bash
python -m venv .venv
source .venv/bin/activate
```

4. Install dependencies

```bash
pip install -r requirements.txt
```

5. Make migrations and migrate

```bash
python manage.py makemigrations
python manage.py migrate
```

6. Create admin/superuser

```bash
python manage.py createsuperuser
```

7. Finally, run the project

```bash
python manage.py runserver 9000
```
