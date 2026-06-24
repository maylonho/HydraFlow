# HydraFlow

HydraFlow is a full-stack productivity and task management platform designed to consolidate practical experience in modern software engineering, including backend development, web and mobile application architecture, automated testing, software quality, and DevOps practices.

The platform consists of:

- A RESTful backend API built with Spring Boot
- A cross-platform mobile application developed with React Native
- A web client built with Next.js
- An automated testing suite implemented with Pytest

HydraFlow enables users to manage tasks, organize priorities, track productivity metrics, and visualize performance through both mobile and web interfaces.

---

## Architecture

HydraFlow follows a distributed client-server architecture composed of four main layers:

- **Web Client**: Browser-based dashboard and analytics platform
- **Mobile Client**: Cross-platform application for daily task management
- **Backend API**: Business logic, authentication, authorization, and persistence
- **Database Layer**: Relational database for structured storage

```text
          Next.js Web Client
                  |
                  |
React Native Mobile Client
                  |
                  |
         Spring Boot REST API
                  |
                  |
                MySQL
```

---

## Tech Stack

### Backend
- Java 21
- Spring Boot
- Spring Security
- Spring Data JPA
- Hibernate
- JWT Authentication
- Maven

### Web
- Next.js
- React
- TypeScript
- Axios
- Tailwind CSS
- Zustand

### Mobile
- React Native
- Expo
- TypeScript
- React Navigation
- Axios
- Zustand

### Database
- MySQL

### Testing
- Python
- Pytest
- Requests
- Fixtures
- Integration Testing
- API Testing

### DevOps
- Docker
- Docker Compose
- GitHub Actions

---

## Features

### Authentication
- User registration
- Secure login
- JWT-based authentication
- Protected routes

### Task Management
- Create tasks
- Update tasks
- Delete tasks
- Mark tasks as completed
- Assign priority levels
- Due date management

### Task Organization
- Categories
- Subtasks / checklists
- Filtering
- Search

### Mobile Features
- Daily task management
- Task completion tracking
- Productivity workflow
- Push notifications (future)

### Web Features
- Analytics dashboard
- Productivity metrics
- Charts and reports
- Administrative management

---

## Repository Structure

HydraFlow uses a monorepo strategy to centralize all application layers.

```bash
hydraflow/
│
├── backend/
├── mobile/
├── web/
├── tests/
├── docs/
├── scripts/
├── docker-compose.yml
├── .env.example
└── README.md
```

### Directory Responsibilities

- **backend/** → Spring Boot REST API
- **mobile/** → React Native application
- **web/** → Next.js web client
- **tests/** → Automated tests with Pytest
- **docs/** → Technical documentation
- **scripts/** → Utility scripts and automation

---

## Backend Architecture

The backend follows a layered architecture to improve maintainability and separation of concerns.

```text
controller/
service/
repository/
entity/
dto/
mapper/
security/
config/
exception/
```

### Layer Responsibilities

#### Controller
Handles HTTP requests and responses.

#### Service
Contains business rules and application logic.

#### Repository
Handles persistence and database access using JPA.

#### Entity
Represents database models.

#### DTO
Encapsulates request and response payloads.

#### Security
Handles authentication and authorization.

#### Exception
Centralizes error handling.

---

## Database Model

### users

| Column | Type |
|--------|------|
| id | UUID |
| name | VARCHAR |
| email | VARCHAR |
| password | VARCHAR |

### tasks

| Column | Type |
|--------|------|
| id | UUID |
| title | VARCHAR |
| description | TEXT |
| priority | ENUM |
| due_date | DATE |
| completed | BOOLEAN |
| user_id | UUID |

### subtasks

| Column | Type |
|--------|------|
| id | UUID |
| description | VARCHAR |
| completed | BOOLEAN |
| task_id | UUID |

---

## API Endpoints

### Authentication

```http
POST /api/auth/register
POST /api/auth/login
```

### Tasks

```http
GET    /api/tasks
POST   /api/tasks
PUT    /api/tasks/{id}
DELETE /api/tasks/{id}
PATCH  /api/tasks/{id}/complete
```

### Dashboard

```http
GET /api/dashboard
```

---

## Testing Strategy

Automated tests are written using Pytest to validate API behavior independently from implementation details.

### Test Categories

#### Unit Tests
Validate isolated business rules.

#### Integration Tests
Validate API communication with database and service layer.

#### End-to-End Tests
Validate complete workflows:

- User registration
- Authentication
- Task creation
- Task completion

Example:

```python
def test_create_task(auth_token):
    payload = {
        "title": "Study Spring Boot",
        "priority": "HIGH"
    }

    response = requests.post(
        "/api/tasks",
        json=payload
    )

    assert response.status_code == 201
```

---

## Quality Goals

This project focuses on software quality attributes such as:

- Maintainability
- Scalability
- Testability
- Security
- Performance
- Reliability

Quality assurance practices include:

- Automated testing
- Code review
- Static analysis
- CI/CD validation
- Continuous refactoring

---

## CI/CD Pipeline

The pipeline automates:

1. Build
2. Test execution
3. Quality validation
4. Deployment

Example workflow:

```text
Push
 ↓
Build
 ↓
Run Tests
 ↓
Quality Validation
 ↓
Deploy
```

---

## Architectural Decisions

### Monorepo Strategy
A monorepo structure was chosen to simplify versioning, documentation, and CI/CD across all application layers.

### Modular Monolith Backend
The backend follows a modular monolith architecture to reduce complexity while preserving separation of concerns.

### Frontend Separation
Two frontend clients were designed for different use cases:

- Mobile-first productivity workflows
- Web-based analytics and administration

### Testing Isolation
Pytest was chosen to validate API behavior independently from backend implementation details.

---

## Future Improvements

- Push notifications
- Offline mode
- AI-based prioritization
- Observability with logs and metrics
- Kubernetes deployment
- Real-time updates using WebSockets

---

## Learning Objectives

This project was created to consolidate practical experience in:

- REST API development with Spring Boot
- Mobile development with React Native
- Modern web development with Next.js
- Authentication and authorization
- Automated testing with Pytest
- CI/CD pipelines
- Containerization with Docker
- Full-stack software architecture
- Software quality engineering

---

## License

This project is for educational and portfolio purposes.