# Intelligent E-commerce Platform (Recommendation Engine)

Production-style e-commerce application featuring an intelligent product recommendation engine, built as a Master’s thesis project.

> **Goal:** demonstrate end-to-end full-stack skills: architecture, REST API, security, data modeling, and recommendation logic.

---

## Key Features

- Product catalog (categories, search, filtering)
- User accounts & authentication (JWT / session)*
- Shopping cart & checkout flow
- Orders history and order management
- Admin management (products, categories, orders)*
- **Recommendation engine**:
  - personalized suggestions based on user interactions (views / cart / purchases)*
  - fallback strategy for cold-start users (popular / trending / similar-category)*
- Basic observability & error handling (logs, consistent API errors)
- Docker-ready local environment*

\* Adjust this list to what is actually implemented.

---

## Tech Stack

**Frontend**
- Angular (TypeScript), RxJS
- UI: (fill: Angular Material / NG-ZORRO / custom)

**Backend**
- Spring Boot (Java)
- REST API (JSON)
- Security: (fill: Spring Security + JWT / sessions)

**Database**
- MongoDB (collections: users, products, orders, interactions)

**DevOps**
- Docker / Docker Compose
- (optional) Nginx reverse proxy

---

## Architecture (High Level)

Frontend (Angular) communicates with Backend (Spring Boot) via REST API.
Backend persists domain data in MongoDB and stores user interaction signals used by the recommendation module.

**Modules**
- `auth` – login/register, token handling
- `catalog` – products & categories
- `orders` – checkout & order lifecycle
- `recommendations` – scoring + ranking + fallback strategies
- `admin` – management endpoints

---

## Recommendation Engine (Short Explanation)

The recommendation logic combines:
- **user-based signals** (recent views/cart/purchases)
- **item similarity** (category/tags/attributes)
- **fallback policies** for cold-start (popular products / trending)

Output is a ranked list of product IDs returned through a dedicated endpoint:
- `GET /api/recommendations` (personalized)
- `GET /api/recommendations/popular` (fallback)

> Keep it simple and explainable: recruiters value clarity and correctness over “ML buzzwords”.

---

## API Overview (examples)

> Replace endpoints with real ones from your project.

- `GET /api/products`
- `GET /api/products/{id}`
- `GET /api/categories`
- `POST /api/auth/login`
- `POST /api/orders`
- `GET /api/orders/me`
- `GET /api/recommendations`

---

## Getting Started (Local)

### Option A — Docker (recommended)

1. Create environment file:
   ```bash
   cp .env.example .env
