# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teachers can log in and then sign up/unregister students
- Students can view activities and participants without logging in

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| GET    | `/auth/me`                                                        | Get current teacher authentication status                           |
| POST   | `/auth/login`                                                     | Log in as a teacher                                                 |
| POST   | `/auth/logout`                                                    | Log out current teacher session                                     |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up a student (teacher login required)                          |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student (teacher login required)                      |

## Teacher Accounts

Teacher usernames and passwords are stored in `teachers.json` and validated by the backend during login.

Example accounts included:

- `ms.johnson` / `teach123`
- `mr.lee` / `teach123`

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
