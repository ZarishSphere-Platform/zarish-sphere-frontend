# Quick Start Guide

Get ZarishSphere Platform running in 5 minutes.

## Prerequisites

- Docker and Docker Compose installed
- 8GB RAM minimum
- 20GB disk space

## Option 1: Docker Compose (Recommended)

### Step 1: Clone Repository

```bash
git clone https://github.com/ZarishSphere-Platform/zarish-sphere-frontend.git
cd zarish-sphere-frontend
```

### Step 2: Start Services

```bash
docker-compose up -d
```

This starts:
- PostgreSQL database
- zarish-fin (Port 8081)
- zarish-hra (Port 8082)
- zarish-his (Port 8083)
- zarish-connect API Gateway (Port 8080)

### Step 3: Verify

```bash
# Check health
curl http://localhost:8080/health

# Test Financial API
curl http://localhost:8080/api/fin/api/v1/journal-entries

# Test HR API
curl http://localhost:8080/api/hra/api/v1/employees

# Test Hospital API
curl http://localhost:8080/api/his/api/v1/patients
```

## Option 2: Manual Setup

### Step 1: Start PostgreSQL

```bash
docker run -d \
  --name zarish-postgres \
  -e POSTGRES_PASSWORD=postgres \
  -p 5432:5432 \
  postgres:15-alpine
```

### Step 2: Start Services

```bash
# Terminal 1 - Financial Service
git clone https://github.com/ZarishSphere-Platform/zarish-fin.git
cd zarish-fin
go run cmd/server/main.go

# Terminal 2 - HR Service
git clone https://github.com/ZarishSphere-Platform/zarish-hra.git
cd zarish-hra
go run cmd/server/main.go

# Terminal 3 - Hospital Service
git clone https://github.com/ZarishSphere-Platform/zarish-his.git
cd zarish-his
go run cmd/server/main.go

# Terminal 4 - API Gateway
git clone https://github.com/ZarishSphere-Platform/zarish-connect.git
cd zarish-connect
go run cmd/server/main.go
```

## First API Calls

### Create a Patient

```bash
curl -X POST http://localhost:8080/api/his/api/v1/patients \
  -H "Content-Type: application/json" \
  -d '{
    "first_name": "John",
    "last_name": "Doe",
    "mrn": "MRN001",
    "gender": "male",
    "birth_date": "1990-01-01T00:00:00Z"
  }'
```

### Create an Employee

```bash
curl -X POST http://localhost:8080/api/hra/api/v1/employees \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jane Smith",
    "work_email": "jane@hospital.com",
    "job_title": "Nurse"
  }'
```

### Create a Journal Entry

```bash
curl -X POST http://localhost:8080/api/fin/api/v1/journal-entries \
  -H "Content-Type: application/json" \
  -d '{
    "name": "INV-001",
    "date": "2025-01-01T00:00:00Z",
    "state": "draft"
  }'
```

## Next Steps

- [Architecture Overview](../architecture/overview.md)
- [Module Documentation](../modules/zarish-fin.md)
- [API Reference](../api/financial.md)
- [Docker Deployment](docker.md)
- [Kubernetes Deployment](kubernetes.md)

## Troubleshooting

### Port Already in Use

```bash
# Check what's using the port
lsof -i :8080

# Kill the process
kill -9 <PID>
```

### Database Connection Failed

```bash
# Check PostgreSQL is running
docker ps | grep postgres

# Check logs
docker logs zarish-postgres
```

### Service Won't Start

```bash
# Check Go version
go version  # Should be 1.21+

# Clean and rebuild
go clean
go mod download
go build
```
