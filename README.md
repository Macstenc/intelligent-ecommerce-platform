# Intelligent E-commerce Platform (Recommendation Engine)

Production-style e-commerce application featuring an intelligent product
recommendation engine, built as a Master's thesis project.

> Goal: Demonstrate full-stack architecture, REST API design, security,
> database modeling, and recommendation logic in a production-like
> environment.

------------------------------------------------------------------------

## Key Features

-   Product catalog (categories, search, filtering)
-   User accounts & authentication (JWT / session-based)
-   Shopping cart & checkout flow
-   Orders history and management
-   Admin product management
-   Intelligent recommendation engine:
    -   Personalized suggestions based on user interactions
    -   Fallback strategy for cold-start users (popular / trending)
-   RESTful API design
-   Docker-ready environment

------------------------------------------------------------------------

## Tech Stack

### Frontend

-   Angular (TypeScript)
-   RxJS
-   UI: (adjust to your library if used)

### Backend

-   Spring Boot (Java)
-   Spring Security
-   REST API (JSON)

### Database

-   MongoDB

### DevOps

-   Docker
-   Docker Compose
-   Optional Nginx reverse proxy

------------------------------------------------------------------------

## Architecture Overview

Frontend (Angular) communicates with Backend (Spring Boot) via REST API.
Backend persists domain data in MongoDB and stores interaction signals
for recommendation logic.

Modules: - auth -- login/register, token handling - catalog -- products
& categories - orders -- checkout & order lifecycle - recommendations --
scoring + ranking + fallback - admin -- management endpoints

------------------------------------------------------------------------

## Recommendation Engine

The recommendation system combines: - User interaction history (views,
cart, purchases) - Category similarity - Popular product fallback

Endpoints example: - GET /api/recommendations - GET
/api/recommendations/popular

------------------------------------------------------------------------

## Getting Started

### Option A --- Docker (Recommended)

Run the stack:

``` bash
docker compose up --build
```

Open:

Frontend: http://localhost:4200\
Backend: http://localhost:8080

------------------------------------------------------------------------

### Option B --- Run without Docker

#### Backend

``` bash
# from backend directory
./mvnw spring-boot:run
```

#### Frontend

``` bash
# from frontend directory
npm ci
npm start
```

------------------------------------------------------------------------

## Environment Variables

Create `.env` based on `.env.example`.

### Example `.env.example`

``` env
# Backend
SPRING_PROFILES_ACTIVE=local
JWT_SECRET=change-me
JWT_EXPIRATION_SECONDS=3600

# MongoDB
MONGO_HOST=localhost
MONGO_PORT=27017
MONGO_DB=ecommerce
MONGO_USER=
MONGO_PASSWORD=

# Frontend (if applicable)
API_BASE_URL=http://localhost:8080/api
```

Never commit real secrets. Use environment-based configuration in
production.

------------------------------------------------------------------------

## API Overview (Example)

-   GET /api/products
-   GET /api/products/{id}
-   GET /api/categories
-   POST /api/auth/login
-   POST /api/orders
-   GET /api/orders/me
-   GET /api/recommendations

------------------------------------------------------------------------

## Security Considerations

-   JWT authentication
-   Role-based authorization
-   Input validation (DTO validation)
-   CORS configured explicitly
-   No stack traces exposed in production
-   Environment-based secret management

------------------------------------------------------------------------

## Accessibility (Frontend)

-   Semantic HTML
-   Visible focus states
-   Keyboard navigation support
-   Proper form labels
-   Accessible buttons and interactive elements

------------------------------------------------------------------------

## Suggested Improvements

-   Add unit tests (backend)
-   Add E2E tests (frontend)
-   Add CI pipeline (GitHub Actions)
-   Improve recommendation explainability
-   Add performance optimization (indexes in MongoDB)

------------------------------------------------------------------------

## Project Status

Portfolio project prepared for recruitment purposes.
