# Architecture Overview

## System Architecture

ZarishSphere Platform follows a **microservices architecture** with clear separation of concerns.

## High-Level Architecture

```mermaid
C4Context
    title System Context Diagram - ZarishSphere Platform
    
    Person(doctor, "Doctor", "Healthcare Provider")
    Person(patient, "Patient", "Healthcare Consumer")
    Person(admin, "Administrator", "System Admin")
    
    System(zarish, "ZarishSphere Platform", "Integrated ERP/EHR System")
    
    System_Ext(fhir, "External FHIR Servers", "HL7 FHIR Resources")
    System_Ext(terminology, "Terminology Services", "SNOMED CT, ICD-11, LOINC")
    
    Rel(doctor, zarish, "Uses", "HTTPS")
    Rel(patient, zarish, "Uses", "HTTPS")
    Rel(admin, zarish, "Manages", "HTTPS")
    
    Rel(zarish, fhir, "Exchanges data", "FHIR API")
    Rel(zarish, terminology, "Validates codes", "REST API")
```

## Microservices Architecture

```mermaid
graph LR
    subgraph "Client Layer"
        WEB[Web Browsers]
        MOBILE[Mobile Apps]
    end
    
    subgraph "API Gateway Layer"
        GW[zarish-connect<br/>Reverse Proxy<br/>CORS Handler]
    end
    
    subgraph "Service Layer"
        subgraph "ERP Services"
            FIN[Financial]
            HR[Human Resources]
            LOG[Logistics]
        end
        
        subgraph "EHR Services"
            HIS[Hospital IS]
            FHIR[FHIR Core]
        end
        
        subgraph "Platform Services"
            AUTH[Authentication]
            TERM[Terminology]
            FORM[Forms]
            GEO[Geography]
            SUP[Support]
            MGT[Management]
            WIKI[Knowledge Base]
            ANALYTICS[Analytics]
        end
    end
    
    subgraph "Data Layer"
        POSTGRES[(PostgreSQL)]
        CACHE[(Redis Cache)]
    end
    
    WEB --> GW
    MOBILE --> GW
    
    GW --> FIN
    GW --> HR
    GW --> LOG
    GW --> HIS
    GW --> FHIR
    GW --> AUTH
    GW --> TERM
    GW --> FORM
    GW --> GEO
    GW --> SUP
    GW --> MGT
    GW --> WIKI
    GW --> ANALYTICS
    
    FIN --> POSTGRES
    HR --> POSTGRES
    LOG --> POSTGRES
    HIS --> POSTGRES
    FHIR --> POSTGRES
    AUTH --> POSTGRES
    TERM --> POSTGRES
    FORM --> POSTGRES
    GEO --> POSTGRES
    SUP --> POSTGRES
    MGT --> POSTGRES
    WIKI --> POSTGRES
    ANALYTICS --> POSTGRES
    
    AUTH --> CACHE
    
    style GW fill:#4F46E5
    style POSTGRES fill:#EF4444
    style CACHE fill:#F59E0B
```

## Service Communication

```mermaid
sequenceDiagram
    participant Client
    participant Gateway as API Gateway
    participant Auth as zarish-access
    participant Service as zarish-his
    participant DB as PostgreSQL
    
    Client->>Gateway: HTTP Request
    Gateway->>Auth: Validate Token
    Auth->>Auth: Check Permissions
    Auth-->>Gateway: Token Valid
    Gateway->>Service: Forward Request
    Service->>DB: Query Data
    DB-->>Service: Return Data
    Service-->>Gateway: Response
    Gateway-->>Client: HTTP Response
```

## Data Flow

```mermaid
flowchart TD
    A[User Request] --> B{API Gateway}
    B --> C{Authentication}
    C -->|Valid| D[Route to Service]
    C -->|Invalid| E[Return 401]
    D --> F{Service Type}
    F -->|ERP| G[Financial/HR/Logistics]
    F -->|EHR| H[Hospital/FHIR]
    F -->|Platform| I[Auth/Forms/etc]
    G --> J[Database Query]
    H --> J
    I --> J
    J --> K[Process Data]
    K --> L[Return Response]
    L --> M[API Gateway]
    M --> N[Client]
```

## Technology Decisions

### Backend: Go

- **Performance**: Compiled language, fast execution
- **Concurrency**: Built-in goroutines for handling multiple requests
- **Type Safety**: Strong typing reduces runtime errors
- **Ecosystem**: Rich libraries for web services (Gin, GORM)

### Database: PostgreSQL

- **ACID Compliance**: Ensures data integrity
- **JSON Support**: Native JSONB for flexible schemas
- **Scalability**: Proven at enterprise scale
- **FHIR Support**: Excellent for healthcare data

### API Gateway: Gin

- **Performance**: One of the fastest Go web frameworks
- **Middleware**: Easy to add authentication, logging, CORS
- **Routing**: Clean and intuitive routing

## Security Architecture

```mermaid
graph TB
    subgraph "Security Layers"
        TLS[TLS/HTTPS]
        CORS[CORS Policy]
        AUTH[JWT Authentication]
        RBAC[Role-Based Access Control]
        AUDIT[Audit Logging]
    end
    
    subgraph "Data Security"
        ENCRYPT[Encryption at Rest]
        BACKUP[Automated Backups]
        GDPR[GDPR Compliance]
    end
    
    TLS --> CORS
    CORS --> AUTH
    AUTH --> RBAC
    RBAC --> AUDIT
    
    AUTH --> ENCRYPT
    ENCRYPT --> BACKUP
    BACKUP --> GDPR
```

## Deployment Architecture

```mermaid
graph TB
    subgraph "Production Environment"
        LB[Load Balancer]
        
        subgraph "Kubernetes Cluster"
            subgraph "Namespace: zarish-prod"
                GW_POD[Gateway Pods x3]
                FIN_POD[Financial Pods x2]
                HIS_POD[Hospital Pods x2]
                OTHER_POD[Other Service Pods]
            end
        end
        
        subgraph "Data Tier"
            PG_PRIMARY[(PostgreSQL Primary)]
            PG_REPLICA[(PostgreSQL Replica)]
        end
        
        subgraph "Monitoring"
            PROM[Prometheus]
            GRAF[Grafana]
        end
    end
    
    LB --> GW_POD
    GW_POD --> FIN_POD
    GW_POD --> HIS_POD
    GW_POD --> OTHER_POD
    
    FIN_POD --> PG_PRIMARY
    HIS_POD --> PG_PRIMARY
    OTHER_POD --> PG_PRIMARY
    
    PG_PRIMARY --> PG_REPLICA
    
    GW_POD -.-> PROM
    FIN_POD -.-> PROM
    HIS_POD -.-> PROM
    PROM --> GRAF
```

## Scalability

### Horizontal Scaling

- Each microservice can scale independently
- Stateless services enable easy replication
- Load balancer distributes traffic

### Vertical Scaling

- Database can be upgraded for more resources
- Individual services can be allocated more CPU/memory

### Caching Strategy

- Redis for session management
- API response caching
- Database query result caching

## High Availability

- **Multi-instance deployment**: Each service runs multiple instances
- **Database replication**: Primary-replica setup
- **Health checks**: Automatic pod restart on failure
- **Circuit breakers**: Prevent cascade failures
