# Code Examples Using cURL and Postman – To-Do API

## Example 1 – Get All Tasks using cURL

**Request**
```bash
curl http://localhost:3000/tasks
```

**Response**
```json
[
  {
    "user_id": 1,
    "title": "Grocery shopping",
    "description": "eggs, bacon, gummy bears",
    "due_date": "2025-02-20T17:00",
    "warning": "-10",
    "id": 1
  },
  {
    "user_id": 1,
    "title": "Piano recital",
    "description": "Daughter's first concert appearance",
    "due_date": "2025-04-02T15:00",
    "warning": "-30",
    "id": 2
  },
  {
    "user_id": 2,
    "title": "Oil change",
    "description": "5K auto service",
    "due_date": "2025-03-10T09:00",
    "warning": "-60",
    "id": 3
  },
  {
    "user_id": 3,
    "title": "Get shots for dog",
    "description": "Annual vaccinations for poochy",
    "due_date": "2025-05-11T14:00",
    "warning": "-20",
    "id": 4
  }
]
```

## Example 2 – Create a Task using Postman

**Request**
- Method: POST  
- URL: http://localhost:3000/tasks  
- Headers:
  - Content-Type: application/json  
- Body (JSON):
```json
{
  "user_id": 4,
  "title": "Fix API mismatch",
  "description": "Update example to include proper fields",
  "due_date": "2025-06-15T12:00",
  "warning": "-15"
}
```

**Response**
```json
{
  "user_id": 4,
  "title": "Fix API mismatch",
  "description": "Update example to include proper fields",
  "due_date": "2025-06-15T12:00",
  "warning": "-15",
  "id": 5
}
```
