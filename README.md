# Welcome to Scadable Platform

**A scalable IoT platform for device management, real-time monitoring, and intelligent automation.**

This repository is the central hub for the Scadable engineering team, containing development standards, conventions, and best practices for building our distributed IoT platform.

## 🎯 Platform Overview

Scadable is a microservices-based IoT platform that provides:
- **Device Management**: Complete lifecycle management for IoT devices
- **Real-time Monitoring**: Live data streaming and analytics via MQTT
- **Intelligent Automation**: Serverless functions and AI-powered agentic workflows
- **Facility Operations**: Multi-tenant facility and asset management
- **Historical Data**: Time-series data storage and querying
- **API Gateway**: Unified API layer with authentication and orchestration

## 🏗️ Platform Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     API Gateway Layer                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ service-api  │  │ service-auth │  │ orchestrator │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│                    Core Business Services                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ service-     │  │ service-     │  │ service-     │      │
│  │ device       │  │ facility     │  │ historian    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│              Automation & Intelligence Layer                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ service-faas │  │ service-     │  │ worker-faas  │      │
│  │              │  │ agentics     │  │              │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│                  Data & Communication Layer                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ service-mqtt │  │ service-     │  │ service-     │      │
│  │              │  │ decoder      │  │ live-query   │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│  ┌──────────────┐                                           │
│  │ service-     │                                           │
│  │ notification │                                           │
│  └──────────────┘                                           │
└─────────────────────────────────────────────────────────────┘
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18+ LTS
- **Docker** & Docker Compose
- **PostgreSQL** 14+
- **Redis** 7+
- **MQTT Broker** (Mosquitto/EMQX)
- **Git**

### Setup Development Environment

1. **Clone the platform repositories**:
```bash
# Clone all backend services
git clone https://github.com/scadable/service-api.git
git clone https://github.com/scadable/service-auth.git
git clone https://github.com/scadable/service-orchestrator.git
git clone https://github.com/scadable/service-device.git
git clone https://github.com/scadable/service-facility.git
git clone https://github.com/scadable/service-faas.git
git clone https://github.com/scadable/service-agentics.git
git clone https://github.com/scadable/service-decoder.git
git clone https://github.com/scadable/service-live-query.git
git clone https://github.com/scadable/service-mqtt.git
git clone https://github.com/scadable/service-notification.git
git clone https://github.com/scadable/service-historian.git
git clone https://github.com/scadable/worker-faas.git

# Clone frontend applications
git clone https://github.com/scadable/web-main.git
git clone https://github.com/scadable/web-dashboard.git
git clone https://github.com/scadable/web-docs.git

# Clone shared libraries
git clone https://github.com/scadable/library-react.git
```

2. **Install dependencies**:
```bash
# For each service directory
cd service-<name>
npm install
```

3. **Configure environment variables**:
```bash
# Copy example env files
cp .env.example .env

# Configure database, Redis, and MQTT connections
# See individual service documentation for specific variables
```

4. **Start infrastructure services**:
```bash
# Using Docker Compose (recommended)
docker-compose up -d postgres redis mosquitto

# Or use individual Docker containers
docker run -d -p 5432:5432 postgres:14
docker run -d -p 6379:6379 redis:7
docker run -d -p 1883:1883 -p 9001:9001 eclipse-mosquitto
```

5. **Run database migrations**:
```bash
# For each service with database
cd service-<name>
npm run migrate
```

6. **Start the services**:
```bash
# Development mode with hot reload
npm run dev

# Production mode
npm run build
npm start
```

## 📦 Backend Services

### Core API Services

| Service | Repository | Description |
|---------|-----------|-------------|
| **API Gateway** | [service-api](https://github.com/scadable/service-api) | Main API gateway and routing layer |
| **Authentication** | [service-auth](https://github.com/scadable/service-auth) | User authentication, authorization, and JWT management |
| **Orchestrator** | [service-orchestrator](https://github.com/scadable/service-orchestrator) | Service coordination and workflow management |

### Device & Facility Management

| Service | Repository | Description |
|---------|-----------|-------------|
| **Device Service** | [service-device](https://github.com/scadable/service-device) | IoT device registration, provisioning, and lifecycle management |
| **Facility Service** | [service-facility](https://github.com/scadable/service-facility) | Multi-tenant facility and asset management |
| **Historian** | [service-historian](https://github.com/scadable/service-historian) | Time-series data storage and historical analytics |

### Automation & Intelligence

| Service | Repository | Description |
|---------|-----------|-------------|
| **FaaS Service** | [service-faas](https://github.com/scadable/service-faas) | Serverless function execution and management |
| **Agentic AI** | [service-agentics](https://github.com/scadable/service-agentics) | AI-powered autonomous agents and workflows |
| **FaaS Worker** | [worker-faas](https://github.com/scadable/worker-faas) | Background job processing for serverless functions |

### Data Processing & Communication

| Service | Repository | Description |
|---------|-----------|-------------|
| **MQTT Service** | [service-mqtt](https://github.com/scadable/service-mqtt) | Real-time MQTT message broker integration |
| **Decoder Service** | [service-decoder](https://github.com/scadable/service-decoder) | Protocol decoding and data transformation |
| **Live Query** | [service-live-query](https://github.com/scadable/service-live-query) | Real-time data querying and subscriptions |
| **Notification** | [service-notification](https://github.com/scadable/service-notification) | Multi-channel notification delivery (email, SMS, push) |

## 🌐 Frontend Applications

| Application | Repository | Description |
|-------------|-----------|-------------|
| **Main Website** | [web-main](https://github.com/scadable/web-main) | Public-facing marketing and landing pages |
| **Dashboard** | [web-dashboard](https://github.com/scadable/web-dashboard) | Real-time monitoring and control dashboard |
| **Documentation** | [web-docs](https://github.com/scadable/web-docs) | Platform documentation and API references |

## 📚 Shared Libraries

| Library | Repository | Description |
|---------|-----------|-------------|
| **React Components** | [library-react](https://github.com/scadable/library-react) | Shared React components and UI primitives |

## 🛠️ Development Workflow

### 1. Feature Development

```bash
# Create feature branch
git checkout -b feature/your-feature-name

# Make changes and commit
git add .
git commit -m "feat: add new feature"

# Push and create PR
git push origin feature/your-feature-name
```

### 2. Code Standards

- **Language**: TypeScript/JavaScript (Node.js 18+)
- **Style Guide**: ESLint + Prettier (see `.eslintrc.js`)
- **Testing**: Jest for unit tests, Supertest for integration tests
- **Documentation**: JSDoc for code, OpenAPI for APIs

### 3. Testing Requirements

```bash
# Run unit tests
npm test

# Run integration tests
npm run test:integration

# Run end-to-end tests
npm run test:e2e

# Coverage report
npm run test:coverage
```

### 4. Pull Request Process

1. Create feature branch from `main`
2. Write tests for new functionality
3. Ensure all tests pass (`npm test`)
4. Update documentation if needed
5. Create PR with descriptive title and description
6. Request code review from team members
7. Address review feedback
8. Merge after approval

## 📚 Core Documentation

This repository is organized into several key areas. Start with the Contribution Guidelines.

| Section | Description |
| :--- | :--- |
| **[📜 Contribution Guidelines](./CONTRIBUTING.md)** | **(Start Here)** How to contribute to this repository and all other Scadable projects. This covers our Git workflow, pull request process, and code review standards. |
| **[🤝 Code of Conduct](./CODE_OF_CONDUCT.md)** | Our pledge to maintain an inclusive, respectful, and collaborative environment. All team members are expected to adhere to this code. |
| **[💻 Development Conventions](./docs/conventions.md)** | Technical standards and style guides for writing code. This includes language-specific guides, API design principles, and our testing philosophy. |
| **[🏛️ Architecture](./docs/architecture/)** | High-level architectural principles and documentation for our core systems. Includes our collection of Architectural Decision Records (ADRs). |
| **[🛠️ Tooling & Setup](./docs/tooling/)** | Guides for setting up your local development environment, using our CI/CD pipelines, and other essential developer tools. |

## 🔧 Infrastructure

### Database Schema

- **PostgreSQL**: Primary data store for relational data
- **TimescaleDB**: Time-series data for device metrics
- **Redis**: Caching and session management

### Message Queues

- **MQTT**: Real-time device communication
- **Redis Pub/Sub**: Service-to-service messaging
- **Bull**: Background job processing

### Deployment

- **Docker**: Containerization for all services
- **Kubernetes**: Production orchestration (optional)
- **Docker Compose**: Local development environment
- **GitHub Actions**: CI/CD pipelines

## 🔐 Security

- **Authentication**: JWT-based authentication with refresh tokens
- **Authorization**: Role-based access control (RBAC)
- **API Security**: Rate limiting, input validation, CORS
- **Data Encryption**: TLS/SSL for data in transit, encryption at rest
- **Secrets Management**: Environment variables, never commit secrets

## 📊 Monitoring & Observability

- **Logging**: Structured logging with Winston/Pino
- **Metrics**: Prometheus-compatible metrics
- **Tracing**: Distributed tracing with OpenTelemetry
- **Health Checks**: `/health` and `/ready` endpoints

## 🤝 Contributing

We welcome contributions! Please read our **[Contribution Guidelines](./CONTRIBUTING.md)** before submitting PRs.

### Quick Contribution Checklist

- [ ] Follow code style guidelines (ESLint + Prettier)
- [ ] Write tests for new features
- [ ] Update documentation
- [ ] Create descriptive commit messages
- [ ] Request code review
- [ ] Ensure CI/CD pipeline passes

## 📝 License

This project is proprietary and confidential. All rights reserved.

## 🔗 Resources

- **GitHub Organization**: https://github.com/scadable
- **Issue Tracking**: Use GitHub Issues in respective repositories
- **Discussions**: Use GitHub Discussions for questions
- **Security**: Report security issues to security@scadable.com

## 👥 Team

For questions or support, reach out to:
- **Platform Team**: platform@scadable.com
- **DevOps**: devops@scadable.com
- **Security**: security@scadable.com

---

**Last Updated**: November 21, 2025

**Maintained by**: Scadable Engineering Team
