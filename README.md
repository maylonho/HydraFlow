# NexTask

NexTask is a full-stack task management platform designed to consolidate knowledge in backend development, mobile application architecture, software quality, and automated testing.

The project consists of a RESTful API built with Spring Boot, a cross-platform mobile client developed with React Native, and an automated testing suite implemented using Pytest. The application allows users to manage tasks, organize priorities, track progress, and analyze productivity metrics.

## Architecture

The system follows a distributed client-server architecture composed of three main layers:

- **Mobile Client**: Cross-platform application responsible for user interaction and API consumption
- **Backend API**: RESTful service responsible for business rules, authentication, and persistence
- **Database Layer**: Relational database for structured data storage

```text
React Native App
       |
       v
Spring Boot REST API
       |
       v
 PostgreSQL Database
```

## Tech Stack

### Backend
- Java 21
- Spring Boot
- Spring Web
- Spring Data JPA
- Spring Security
- JWT Authentication
- Hibernate
- Maven

### Mobile
- React Native
- Expo
- TypeScript
- React Navigation
- Axios
- Zustand / Context API

### Database
- PostgreSQL

### Testing
- Python
- Pytest
- Requests
- Pytest Fixtures
- API Integration Testing

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

### Analytics
- Productivity dashboard
- Completion metrics
- Weekly statistics

---

## Backend Architecture

The backend follows a layered architecture to improve maintainability and separation of concerns:

```text
controller/
service/
repository/
entity/
dto/
mapper/
security/
exception/
config/
```

### Layer Responsibilities

#### Controller
Handles HTTP requests and responses.

#### Service
Contains business rules and application logic.

#### Repository
Handles database access using JPA.

#### DTO
Encapsulates request and response payloads.

#### Security
Responsible for authentication and authorization.

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

Automated tests are written using Pytest to validate application behavior.

### Test Categories

#### Unit Tests
Validate isolated business rules.

#### Integration Tests
Validate communication between API and database.

#### End-to-End Tests
Validate complete workflows such as:

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

Quality assurance practices include:

- Automated testing
- Code review
- Static analysis
- CI/CD pipeline

---

## CI/CD Pipeline

The pipeline automates:

1. Build
2. Test execution
3. Quality validation
4. Deployment

Example flow:

```text
Push → Build → Run Tests → Quality Check → Deploy
```

---

## Future Improvements

- Push notifications
- Offline mode
- AI-based prioritization
- Performance monitoring
- Kubernetes deployment
- Observability with logs and metrics

---

## Learning Objectives

This project was created to consolidate practical experience in:

- REST API development
- Mobile application architecture
- Software testing
- Clean architecture
- Secure authentication
- DevOps practices

---

## License

This project is for educational and portfolio purposes.