# zarish-hra - Human Resources Module

**Repository:** [zarish-hra](https://github.com/ZarishSphere-Platform/zarish-hra)  
**Port:** 8082  
**Status:** ✅ Production Ready with Full API

## Features

- Employee management
- Department tracking
- Contact information
- Job titles and roles

## API Endpoints

- `POST /api/v1/employees` - Create employee
- `GET /api/v1/employees/:id` - Get employee
- `GET /api/v1/employees` - List employees

## Data Model

```go
type Employee struct {
    ID          uint
    Name        string
    WorkEmail   string
    JobTitle    string
    Department  string
    Phone       string
}
```
