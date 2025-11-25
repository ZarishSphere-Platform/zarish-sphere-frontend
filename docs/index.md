# ZarishSphere Platform

![ZarishSphere Logo](https://via.placeholder.com/800x200/4F46E5/FFFFFF?text=ZarishSphere+Platform)

## Welcome to ZarishSphere

A comprehensive **ERP/EHR integrated platform** combining enterprise resource planning with electronic health records, built on FHIR standards.

## 🎯 Overview

ZarishSphere Platform is a modern, microservices-based healthcare and business management system that seamlessly integrates:

- **ERP Capabilities**: Financial management, HR, logistics
- **EHR Capabilities**: Patient records, clinical data, FHIR compliance
- **Platform Services**: Authentication, forms, analytics, knowledge base

## 🏗️ Architecture

```mermaid
graph TB
    subgraph "Frontend Layer"
        DP[Doctor Portal]
        PP[Patient Portal]
        LP[Lab Portal]
        PHP[Pharmacy Portal]
        AD[Admin Dashboard]
    end
    
    subgraph "API Gateway"
        GW[zarish-connect<br/>Port 8080]
    end
    
    subgraph "ERP Services"
        FIN[zarish-fin<br/>Financial<br/>Port 8081]
        HRA[zarish-hra<br/>HR<br/>Port 8082]
        LOG[zarish-log<br/>Logistics<br/>Port 8093]
    end
    
    subgraph "EHR Services"
        HIS[zarish-his<br/>Hospital<br/>Port 8083]
        SPH[zarish-sphere<br/>FHIR Core<br/>Port 8084]
    end
    
    subgraph "Platform Services"
        ACC[zarish-access<br/>Auth<br/>Port 8085]
        TRM[zarish-terms<br/>Terminology<br/>Port 8086]
        FRM[zarish-forms<br/>Forms<br/>Port 8087]
        GEO[zarish-geo<br/>Geography<br/>Port 8088]
        SUP[zarish-support<br/>Support<br/>Port 8089]
        MGT[zarish-management<br/>Projects<br/>Port 8090]
        WKI[zarish-wiki<br/>Knowledge<br/>Port 8091]
        INS[zarish-insight<br/>Analytics<br/>Port 8092]
    end
    
    subgraph "Data Layer"
        DB[(PostgreSQL<br/>Database)]
    end
    
    DP --> GW
    PP --> GW
    LP --> GW
    PHP --> GW
    AD --> GW
    
    GW --> FIN
    GW --> HRA
    GW --> HIS
    GW --> SPH
    GW --> ACC
    GW --> TRM
    GW --> FRM
    GW --> GEO
    GW --> SUP
    GW --> MGT
    GW --> WKI
    GW --> INS
    GW --> LOG
    
    FIN --> DB
    HRA --> DB
    HIS --> DB
    SPH --> DB
    ACC --> DB
    TRM --> DB
    FRM --> DB
    GEO --> DB
    SUP --> DB
    MGT --> DB
    WKI --> DB
    INS --> DB
    LOG --> DB
    
    style GW fill:#4F46E5,stroke:#312E81,stroke-width:3px,color:#fff
    style FIN fill:#10B981,stroke:#065F46,stroke-width:2px,color:#fff
    style HRA fill:#10B981,stroke:#065F46,stroke-width:2px,color:#fff
    style LOG fill:#10B981,stroke:#065F46,stroke-width:2px,color:#fff
    style HIS fill:#F59E0B,stroke:#92400E,stroke-width:2px,color:#fff
    style SPH fill:#F59E0B,stroke:#92400E,stroke-width:2px,color:#fff
    style DB fill:#EF4444,stroke:#991B1B,stroke-width:2px,color:#fff
```

## ✨ Key Features

### ERP Modules

- **Financial Management** (`zarish-fin`): Complete accounting, journal entries, chart of accounts
- **Human Resources** (`zarish-hra`): Employee management, departments, payroll
- **Logistics** (`zarish-log`): Inventory, shipment tracking, supply chain

### EHR Modules

- **Hospital Information System** (`zarish-his`): Patient records, encounters, FHIR-compliant
- **FHIR Core** (`zarish-sphere`): Practitioners, organizations, locations

### Platform Services

- **Authentication** (`zarish-access`): User management, roles, permissions
- **Terminology** (`zarish-terms`): SNOMED CT, ICD-11, LOINC
- **Forms** (`zarish-forms`): Dynamic form builder with JSON schema
- **Geography** (`zarish-geo`): Administrative divisions, districts
- **Support** (`zarish-support`): Ticket management system
- **Project Management** (`zarish-management`): Tasks, projects, collaboration
- **Knowledge Base** (`zarish-wiki`): Documentation, articles
- **Analytics** (`zarish-insight`): Dashboards, reports, metrics

## 🚀 Quick Start

### Using Docker Compose

```bash
# Clone the repository
git clone https://github.com/ZarishSphere-Platform/zarish-sphere-frontend.git

# Start all services
docker-compose up -d

# Access the API Gateway
curl http://localhost:8080/health
```

### Manual Setup

```bash
# Start individual services
cd zarish-fin && go run cmd/server/main.go  # Port 8081
cd zarish-hra && go run cmd/server/main.go  # Port 8082
cd zarish-his && go run cmd/server/main.go  # Port 8083
cd zarish-connect && go run cmd/server/main.go  # Port 8080
```

## 📊 Technology Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Go 1.21+, Gin, GORM |
| **Database** | PostgreSQL 15 |
| **Frontend** | React, TypeScript, Vite |
| **API** | REST, FHIR R4 |
| **DevOps** | Docker, Kubernetes, GitHub Actions |

## 📖 Documentation

- [Architecture Overview](architecture/overview.md)
- [Module Documentation](modules/zarish-fin.md)
- [API Reference](api/financial.md)
- [Deployment Guide](deployment/quickstart.md)

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](contributing.md).

## 📄 License

Copyright © 2025 ZarishSphere Platform. All rights reserved.

## 🔗 Links

- [GitHub Organization](https://github.com/ZarishSphere-Platform)
- [Documentation](https://zarishsphere-platform.github.io/zarish-sphere-frontend/)
- [API Gateway](http://localhost:8080)
