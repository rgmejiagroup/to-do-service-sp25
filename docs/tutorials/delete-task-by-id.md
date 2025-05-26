# Deleting tasks

The to-do list API allows users to easily delete existing tasks. For example, this capability can delete tasks after completion
or remove tasks that are no longer relevant.

## Prerequisites

* An existing to-do list with tasks
* Access to a command line or Postman
    * This tutorial uses Postman, but can use the command line to make the necessary REST API calls.

## Deleting an existing task

1. Confirm the local To-Do Service is running.
   * If the service isn't running, run the following command:

     ```shell
     cd <your-github-workspace>/to-do-service/api
     json-server -w to-do-db-source.json
```

2. Open the Postman app on your computer.
3. Locate the task you want to delete. For a full list of the tasks currently available in the to-do list, create a new request
   with the following values:
    * **METHOD**: GET
    * **URL**: `{{base_url}}/tasks`
    * **Header**: `Content-Type: application/json`
    * **Request Body**:

    ```json
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
```

4. After locating the task to delete, create a new request with the following values:
    * **METHOD**: DELETE
    * **URL**: `{{base_url}}/tasks/{taskId}`
    * **Header**: `Content-Type: application/json`
    * **Request Body**: `{}`
5. To confirm the task isn't on the to-do list, create a request with the following values:
    * **METHOD**: GET
    * **URL**: `{{base_url}}/tasks/{taskId}`
    * **Header**: `Content-Type: application/json`
    * **Request Body**: `{}`
6. Postman returns the following response if the deletion was successful: `{}`

## Result

You can now locate and delete existing tasks in the to-do list.
