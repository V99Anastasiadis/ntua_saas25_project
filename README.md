# NTUA ECE SaaS 2025 Project - clearSKY

Repository for the project of the NTUA ECE course **Software as a Service Technologies**, spring semester 2024-2025.

The project is about the development of **clearSKY**, a SaaS web application for managing course grades and grade review requests in an educational environment.

## Repository Note

This repository is a re-upload of the original team project developed as part of the Software as a Service Technologies course.

The initial development, including the full commit history and team contributions, was conducted in a private university GitHub organization repository, which could not be transferred to a personal GitHub account. As a result, this repository does not reflect the original commit history.

This version contains the final state of the project, preserving the implemented functionality and the overall structure of the original submission.

## Description

clearSKY is a SaaS web application designed for educational institutions, instructors, and students.

The main goal of the application is to support the process of publishing course grades before they are finalized. Instructors can upload the initial grades of a course, students can view their personal grade, and, if needed, submit a grade review request. The instructor can then review these requests, reply to them, and finally upload the final grades.

The system also supports institution registration, credit management, Google login, user management, and statistics for final course grades.

The application follows a **microservices architecture** and is designed to run using **Docker containers**.

## Main Features

The application supports the following functionality:

- User management
- Google login
- Institution registration
- Credit purchase and management for institutions
- Initial grade upload by instructors
- Personal grade viewing by students
- Final grade statistics
- Grade review requests by students
- Instructor replies to review requests
- Final grade upload by instructors
- Frontend interface for using the application
- Deployment using Docker Compose

## Repository Structure

```text
.
├── View_personal_grades/                 # Service for viewing personal student grades
├── ai-log/                               # AI tool usage logs
├── architecture/                         # Architecture and design documentation
├── credits_service/                      # Service for institution credits
├── final_grades/                         # Service for final grade uploads
├── front-end/                            # Frontend application
├── google_auth_service/                  # Service for Google authentication
├── initial_grades/                       # Service for initial grade uploads
├── instructor_review_reply_service/      # Service for instructor replies to review requests
├── orchestrator/                         # Central orchestration / gateway logic
├── registration_service/                 # Service for institution registration
├── stats_service/                        # Service for grade statistics
├── student_request_review_service/       # Service for student review requests
├── user_management_service/              # Service for user management
├── docker-compose.yml                    # Docker Compose configuration
├── all.sh                                # Helper script for running the project
├── front-end.sh                          # Helper script for the frontend
├── LICENSE
└── README.md
```

## Technologies Used

The project uses the following technologies:

- **Go** for part of the backend services
- **JavaScript / Node.js** for backend services and application logic
- **EJS** for server-side rendered views
- **CSS** for styling
- **Docker** for containerization
- **Docker Compose** for running the complete application
- **GitHub** for source code management and project management
- **AI tools** for development and documentation support

## Architecture

The application is implemented using a **microservices architecture**.

Each main feature is implemented as a separate service. This makes the project easier to split into independent parts and allows each service to focus on a specific responsibility.

The main services are:

- Google authentication service
- User management service
- Institution registration service
- Credits service
- Initial grades service
- Personal grades service
- Student review request service
- Instructor review reply service
- Final grades service
- Statistics service
- Orchestrator service
- Frontend application

The `orchestrator/` service acts as a central coordination point between the frontend and the individual backend services.

The services run inside Docker containers and communicate through the Docker network.

## Services

### Google Auth Service

Folder:

```text
google_auth_service/
```

This service handles login through Google authentication.

### User Management Service

Folder:

```text
user_management_service/
```

This service handles user-related operations, such as user information, roles, and account management.

### Registration Service

Folder:

```text
registration_service/
```

This service handles institution registration and onboarding-related functionality.

### Credits Service

Folder:

```text
credits_service/
```

This service manages institution credits. Credits are used by institutions in order to use the clearSKY service for their courses.

### Initial Grades Service

Folder:

```text
initial_grades/
```

This service handles the upload and management of initial course grades by instructors.

### View Personal Grades Service

Folder:

```text
View_personal_grades/
```

This service allows students to view their personal grades.

### Student Request Review Service

Folder:

```text
student_request_review_service/
```

This service allows students to submit grade review requests.

### Instructor Review Reply Service

Folder:

```text
instructor_review_reply_service/
```

This service allows instructors to reply to student grade review requests.

### Final Grades Service

Folder:

```text
final_grades/
```

This service handles the upload and management of final course grades.

### Stats Service

Folder:

```text
stats_service/
```

This service provides statistics based on final course grades.

### Orchestrator

Folder:

```text
orchestrator/
```

The orchestrator coordinates communication between the frontend and the backend services. It works as a central access point for the main application flows.

## Typical User Flow

A typical use case of the application is the following:

1. A user logs in to the system.
2. An institution registers to the service.
3. The institution purchases or receives credits.
4. An instructor uploads the initial grades of a course.
5. A student logs in and views their personal grade.
6. If needed, the student submits a grade review request.
7. The instructor reviews the request and replies.
8. The instructor uploads the final grades.
9. Students can view statistics for final course grades.

## Grade Files

The application is based on the idea that instructors upload grade files in a spreadsheet format.

These files are mainly used for:

- Uploading initial grades
- Uploading final grades
- Viewing personal grades
- Producing final grade statistics

The expected grade file format follows the general structure used by the NTUA student registry system.

## Docker Setup

The project is designed to run using Docker containers.

Before running the project, make sure that the following are installed:

- Docker
- Docker Compose

### Start the application

From the root folder of the repository, run:

```bash
docker compose up --build
```

For older Docker Compose versions:

```bash
docker-compose up --build
```

To run the application in the background:

```bash
docker compose up --build -d
```

### Stop the application

```bash
docker compose down
```

### Stop the application and remove volumes

```bash
docker compose down -v
```

## Running with Helper Scripts

The repository also includes helper shell scripts.

To run the main parts of the project:

```bash
./all.sh
```

To run the frontend:

```bash
./front-end.sh
```

If the scripts do not have execution permissions, run:

```bash
chmod +x all.sh
chmod +x front-end.sh
```

Then run:

```bash
./all.sh
```

## Frontend

The frontend is located in:

```text
front-end/
```

The frontend provides a simple web interface for using the main features of the application.

Through the frontend, users can perform actions such as:

- Logging in
- Viewing grades
- Uploading initial grades
- Submitting grade review requests
- Replying to review requests
- Viewing grade statistics
- Uploading final grades

The frontend communicates with the backend services through the orchestrator or through the corresponding service endpoints.

## AI Log

The `ai-log/` folder contains the recorded use of AI tools during the development of the project.

AI tools were used mainly for:

- Understanding requirements
- Discussing architectural decisions
- Designing the microservices structure
- Debugging
- Improving code
- Writing and improving documentation

## Architecture Documentation

The `architecture/` folder contains files related to the architecture and design of the system.

The documentation may include:

- Class diagrams
- Component diagrams
- Deployment diagrams
- Sequence diagrams
- Data structure diagrams
- Communication flows between services

## Useful Commands

Build and start the application:

```bash
docker compose up --build
```

Start without rebuilding:

```bash
docker compose up
```

Start in detached mode:

```bash
docker compose up -d
```

View logs:

```bash
docker compose logs
```

View logs for a specific service:

```bash
docker compose logs <service_name>
```

Stop the application:

```bash
docker compose down
```

Stop the application and remove volumes:

```bash
docker compose down -v
```

Rebuild a specific service:

```bash
docker compose build <service_name>
```

Restart a specific service:

```bash
docker compose restart <service_name>
```

## Troubleshooting

### Docker does not start

Make sure Docker is running.

```bash
docker --version
docker compose version
```

If Docker Desktop is used, make sure it is open before running the application.

### A service does not start

Check the logs of the specific service:

```bash
docker compose logs <service_name>
```

The issue is usually related to a missing dependency, a wrong environment variable, or a port conflict.

### Port already in use

If a port is already being used by another application, either stop the other application or change the port inside `docker-compose.yml`.

### The frontend does not load correctly

Check that:

- The frontend container is running
- The orchestrator service is running
- The backend services are available
- The frontend uses the correct backend URLs

### A request fails

Check the logs:

```bash
docker compose logs
```

Then check the logs of the related service:

```bash
docker compose logs <service_name>
```

After that, try running the flow again from the frontend.

## Project Deliverables

The repository contains the main deliverables of the project:

- Source code of the application
- Microservices implementation
- Frontend application
- Docker Compose deployment setup
- Helper deployment scripts
- Architecture documentation
- AI usage log
- Final version of the application

## Note About Commit History

The original team repository was created inside a private GitHub organization provided by the university. Since the repository could not be transferred to a personal GitHub account together with its full commit history, this repository was created as a re-upload of the final version.

For this reason, the commit history in this repository does not represent the actual development timeline or the full contribution history of the team. It only contains the final state of the project.

## License

This project is distributed under the MIT License. More information can be found in:

```text
LICENSE
```
