# Financial API Reference

Base URL: `http://localhost:8080/api/fin/api/v1`

## Endpoints

### Journal Entries

#### Create Journal Entry

```http
POST /journal-entries
```

**Request Body:**

```json
{
  "name": "INV-2025-001",
  "date": "2025-01-15T00:00:00Z",
  "state": "draft",
  "move_type": "out_invoice",
  "partner_id": 1,
  "amount": 1000.00
}
```

**Response:** `201 Created`

```json
{
  "id": 1,
  "name": "INV-2025-001",
  "date": "2025-01-15T00:00:00Z",
  "state": "draft",
  "move_type": "out_invoice",
  "partner_id": 1,
  "amount": 1000.00,
  "created_at": "2025-01-15T10:30:00Z",
  "updated_at": "2025-01-15T10:30:00Z"
}
```

#### Get Journal Entry

```http
GET /journal-entries/{id}
```

**Response:** `200 OK`

```json
{
  "id": 1,
  "name": "INV-2025-001",
  "date": "2025-01-15T00:00:00Z",
  "state": "draft",
  "move_type": "out_invoice",
  "amount": 1000.00,
  "lines": [
    {
      "id": 1,
      "account_id": 101,
      "name": "Product Sale",
      "debit": 0,
      "credit": 1000.00
    }
  ]
}
```

#### List Journal Entries

```http
GET /journal-entries?page=1&page_size=10
```

**Query Parameters:**

- `page`: Page number (default: 1)
- `page_size`: Items per page (default: 10)

**Response:** `200 OK`

```json
[
  {
    "id": 1,
    "name": "INV-2025-001",
    "date": "2025-01-15T00:00:00Z",
    "state": "draft",
    "amount": 1000.00
  },
  {
    "id": 2,
    "name": "INV-2025-002",
    "date": "2025-01-16T00:00:00Z",
    "state": "posted",
    "amount": 2500.00
  }
]
```

## Data Models

### AccountMove

| Field | Type | Description |
|-------|------|-------------|
| id | integer | Unique identifier |
| name | string | Journal entry number |
| date | datetime | Accounting date |
| state | string | draft, posted, cancelled |
| move_type | string | entry, out_invoice, in_invoice |
| partner_id | integer | Related partner ID |
| amount | float | Total amount |
| created_at | datetime | Creation timestamp |
| updated_at | datetime | Last update timestamp |

### AccountMoveLine

| Field | Type | Description |
|-------|------|-------------|
| id | integer | Unique identifier |
| move_id | integer | Parent journal entry |
| account_id | integer | Chart of accounts reference |
| name | string | Line description |
| debit | float | Debit amount |
| credit | float | Credit amount |
| balance | float | Running balance |

## Error Responses

### 400 Bad Request

```json
{
  "error": "Invalid request body"
}
```

### 404 Not Found

```json
{
  "error": "Journal entry not found"
}
```

### 500 Internal Server Error

```json
{
  "error": "Internal server error"
}
```

## Examples

### cURL

```bash
# Create journal entry
curl -X POST http://localhost:8080/api/fin/api/v1/journal-entries \
  -H "Content-Type: application/json" \
  -d '{
    "name": "INV-001",
    "date": "2025-01-01T00:00:00Z",
    "state": "draft",
    "amount": 1000.00
  }'

# Get journal entry
curl http://localhost:8080/api/fin/api/v1/journal-entries/1

# List journal entries
curl http://localhost:8080/api/fin/api/v1/journal-entries?page=1&page_size=10
```

### JavaScript

```javascript
// Create journal entry
const response = await fetch('http://localhost:8080/api/fin/api/v1/journal-entries', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    name: 'INV-001',
    date: '2025-01-01T00:00:00Z',
    state: 'draft',
    amount: 1000.00
  })
});

const data = await response.json();
console.log(data);
```

### Python

```python
import requests

# Create journal entry
response = requests.post(
    'http://localhost:8080/api/fin/api/v1/journal-entries',
    json={
        'name': 'INV-001',
        'date': '2025-01-01T00:00:00Z',
        'state': 'draft',
        'amount': 1000.00
    }
)

data = response.json()
print(data)
```
