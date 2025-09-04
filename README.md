# 🚀 FastAPI Microservices Boilerplate  

A **cloud-native microservices boilerplate** built with **FastAPI** and Python, showcasing **enterprise-grade architecture, clean separation of concerns, and reusable shared libraries**.  

This project demonstrates how to design, structure, and deploy **distributed systems** that are:  
- Modular  
- Scalable  
- Testable  
- Cloud-ready  

---

## 📂 Repository Structure

```bash
fastapi-microservices/
├── services/                   # Independent microservices (each deployable independently)
│   ├── auth-service/           # Authentication & authorization
│   │   ├── src/
│   │   │   ├── api/            # REST/RPC endpoints (FastAPI routers)
│   │   │   ├── core/           # Business logic, domain services
│   │   │   ├── models/         # SQLAlchemy ORM or Pydantic models
│   │   │   ├── schemas/        # Pydantic request/response DTOs
│   │   │   ├── infra/          # DB, cache, external clients
│   │   │   ├── config.py       # Loads from env (Pydantic BaseSettings)
│   │   │   ├── dependencies.py # FastAPI DI wiring
│   │   │   └── main.py         # FastAPI entrypoint
│   │   ├── alembic/            # DB migrations
│   │   ├── tests/              # Unit tests
│   │   └── Dockerfile
│   │
│   ├── posts-service/          # Example domain service
│   │   ├── src/
│   │   │   ├── api/
│   │   │   ├── core/
│   │   │   ├── models/
│   │   │   ├── schemas/
│   │   │   ├── infra/
│   │   │   ├── config.py
│   │   │   └── main.py
│   │   ├── alembic/
│   │   ├── tests/
│   │   └── Dockerfile
│   │
│   └── aws-service/            # Example external integration service (S3, SES, etc.)
│       ├── src/
│       └── ...
│
├── shared/                     # Common reusable libraries (usable by ANY service)
│   ├── libs/
│   │   ├── common/             # Logging, tracing, middlewares, error handling
│   │   ├── auth/               # JWT utils, token parsing, RBAC enforcement
│   │   ├── db/                 # SQLAlchemy base, DB sessions, migration helpers
│   │   ├── messaging/          # Kafka/RabbitMQ/NATS client wrappers
│   │   └── settings/           # Centralized config loaders (Pydantic BaseSettings)
│   └── contracts/              # API schemas: OpenAPI, AsyncAPI, protobuf, Avro
│
├── gateway/                    # API Gateway (single entry point for clients)
│   ├── src/
│   │   ├── api-gateway.py      # Routes requests → services (REST/gRPC)
│   │   └── auth-middleware.py  # JWT validation, rate limiting
│   └── Dockerfile
│
├── infra/                      # Infrastructure as Code
│   ├── k8s/                    # Kubernetes manifests / Helm charts
│   ├── terraform/              # Cloud infra provisioning (DBs, queues, VPC, secrets)
│   └── docker-compose.yml      # Local development orchestration
│
├── observability/              # Monitoring & logging stack
│   ├── grafana/                # Dashboards
│   ├── prometheus/             # Metrics scraping
│   ├── jaeger/                 # Distributed tracing
│   └── logging/                # Centralized log config
│
├── tests/                      # Global tests
│   └── integration/            # Cross-service integration tests
│
├── .github/workflows/          # CI/CD pipelines (GitHub Actions / Azure DevOps)
├── requirements/               # Dependency management
│   ├── base.txt
│   ├── dev.txt
│   └── prod.txt
└── README.md
```

---

## ✨ Features  

- 🏗 **Microservice architecture** — each service is independent, with its own DB schema, migrations, and deployment pipeline.  
- 🔑 **Authentication & RBAC** — central `auth-service` with JWT & OAuth2.  
- 📡 **API Gateway** — single entry point for routing, auth, and rate limiting.  
- 🌍 **Reusable shared libraries** — logging, configs, DB base, messaging, and auth utilities available to all services.  
- 📊 **Observability** — Prometheus metrics, Grafana dashboards, Jaeger tracing, centralized logging.  
- ⚡ **Infrastructure as Code** — Kubernetes manifests, Terraform, and Docker Compose for local development.  
- 🔄 **Event-driven communication** — Kafka/RabbitMQ/NATS ready.  
- 🧪 **Testing strategy** — unit tests per service + integration tests across services.  
- 🚀 **CI/CD pipelines** — automated build, test, lint, security checks, migrations, and deploy.  

---

## 🛠️ Tech Stack  

- **Backend Framework**: FastAPI, Pydantic, SQLAlchemy  
- **Databases**: PostgreSQL (per service schema)  
- **Messaging**: Kafka / RabbitMQ / NATS  
- **Auth**: JWT, OAuth2, RBAC  
- **Infra**: Docker, Kubernetes, Terraform  
- **Observability**: Prometheus, Grafana, Jaeger, Centralized logging  
- **CI/CD**: GitHub Actions, Azure DevOps  


---

## ⚙️ Getting Started  

### 1️⃣ Clone repo  
git clone https://github.com/<your-username>/fastapi-microservices.git
cd fastapi-microservices

### 2️⃣ Start locally with Docker Compose
docker-compose up --build

### 3️⃣ Access services

API Gateway → http://localhost:8000

Auth Service → http://localhost:8001/docs

Posts Service → http://localhost:8002/docs

---

## 🧪 Running Tests

### Unit tests (inside a service):
cd services/auth-service
pytest

### Integration tests (cross-service):
pytest tests/integration

---

## 📈 Architecture Diagram
```bash
          ┌───────────────┐
          │   API Gateway │
          └───────┬───────┘
                  │
     ┌────────────┼────────────┐
     │            │            │
┌────▼─────┐ ┌────▼─────┐ ┌────▼─────┐
│ Auth     │ │ Posts    │ │ AWS      │
│ Service  │ │ Service  │ │ Service  │
└────┬─────┘ └────┬─────┘ └────┬─────┘
     │            │            │
     └──────► Shared Libraries ◄──────┘
```

---

## 🎯 Why This Repo?

This repo is designed to showcase professional system design skills and serve as a reference architecture for Python + FastAPI microservices.

It highlights:

✅ Clean domain separation

✅ Shared reusable libraries (common code, contracts, infra)

✅ Cloud-native deployment model

✅ Observability and DevOps best practices

---

## 👤 Author
Gurminder Sohi
Senior Software Engineer | Full-stack | Cloud & AI Enthusiast

🔗 [LinkedIn](https://www.linkedin.com/in/gurmindersohi/)