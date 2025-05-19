# Update a Task Using PATCH

This tutorial shows you how to update an existing task using the PATCH method of the To-Do API. This is helpful when you want to update just one or two fields of a task — like marking it complete or changing the title — without sending the entire object.

## Goal

Update an existing task’s `title` or `completed` status using the PATCH `/tasks/{taskId}` endpoint.

## Prerequisites

Before you begin, make sure you have:

- A running instance of the To-Do API on `localhost:3000`
- At least one task already created (so you have a task ID)
- A tool like `curl` or Postman

## Example Request Using `curl`

```bash
curl -X PATCH http://localhost:3000/tasks/1 ^
  -H "Content-Type: application/json" ^
  -d "{\"completed\": true}"