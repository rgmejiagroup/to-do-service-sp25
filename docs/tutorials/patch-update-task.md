# Update a Task Using `PATCH`

This tutorial shows you how to update an existing task using the `PATCH` method of the To-Do API. This is helpful when you want to update just one or two fields of a task — like marking it complete or changing the title — without sending the entire object.

## Goal

Update an existing task’s `title` or `completed` status using the `PATCH` `/tasks/{taskId}` endpoint.

## Prerequisites

Before you begin, make sure you have:

- A running instance of the To-Do API on `localhost:3000`
- At least one task already created (so you have a task ID)
- A tool like `curl` or Postman

---

## Example 1 – Using `curl`

```bash
curl -X PATCH http://localhost:3000/tasks/1 \
  -H "Content-Type: application/json" \
  -d "{\"completed\": true}"

### Expected Response

```json
{
  "id": 1,
  "title": "Sample Task",
  "completed": true
}
```

## Example 2 – Using Postman

1. Open Postman and select the `PATCH` method.
2. Enter the request URL: `http://localhost:3000/tasks/1`
3. Go to the **Headers** tab and add:
   - Key: `Content-Type`
   - Value: `application/json`
4. Go to the **Body** tab, select `raw`, and choose `JSON` as the format.
5. Enter the following body:

```json
{
  "title": "Updated Task Title"
}
```

###Expected Response

```json
{
  "id": 1,
  "title": "Updated Task Title",
  "completed": false
}
```
