# Code Examples Using cURL and Postman – To-Do API

## Example 1 – Get All Tasks using cURL

**Request**
```bash
curl http://localhost:3000/tasks
```

**Response**
[
  {
    "id": 1,
    "title": "Sample Task",
    "completed": false
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
  "title": "New Task from Postman",
  "completed": false
}
```

**Response**
```
{
  "id": 2,
  "title": "New Task from Postman",
  "completed": false
}
```

