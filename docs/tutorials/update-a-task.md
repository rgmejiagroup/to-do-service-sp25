---
layout: page
---

# Tutorial: Update a Task

In this tutorial, you learn the operations to call to
update a to-do item for a user of the service.

Expect this tutorial to take about 15 minutes to complete. The examples in this tutorial assume the API is running locally at `http://localhost:3000`.

## Before you start

* Make sure you've completed the [Before you start a tutorial](../before-you-start-a-tutorial.md) topic on the development system you'll use for the tutorial.

* The local task management API server running at `http://localhost:3000`.

* Before you can update a task, you must first know the unique `id` of the task you want to update. Use the GET method to obtain the `taskId`, which is the unique `id` of a task.

* Ensure you're familiar with REST API concepts and sending HTTP requests.

## Headers

* `Content-Type: application/json`:  Indicates the request body format.
* `Authorization`: None needed for the json-server environment hosting this API.

## Update an existing task

Updating an existing task in the service requires that you use the `PUT` method to store the details of the updated [`task`](../api/task.md) resource. The PUT method requires you to specify all values of a task's properties, even if you aren't updating all values.

Example: You are only updating the value for the `due_date` property of a task. In the response body, you still need to include the entire set of properties, as follows:
*`id` (string) The unique identifier of the task. The `id` in the request body must match the `{taskId}` specified in the URL path. This ensures consistency and validates that you are updating the intended resource.
*`user_id` (string) The unique ID of the user who owns the task. You can update the user_id using PUT as long as it's unique.
*`title`(string) The title of the task.
*`description` (string) A short description of the task.
*`due_date` (string) The date and time the task is due.
    *Format: YYY-MM-DDTHH:mm
    *Example: 2025-12-15T10:30
*`warning`(integer) The trigger value in minutes before the `due_date` for a validation message.
    * Example: `-60` triggers a warning message at 60 minutes before the task's due date and time.

**To update a task:**

1. Make sure your local service is running. Start it by using this command:

    ```shell
    cd <your-github-workspace>/to-do-service/api
    json-server -w to-do-db-source.json
    ```

1. Open the Postman app on your desktop.
1. In the Postman app, create a new request with these values:
    * **METHOD**: PUT
    * **URL**: `{{base_url}}/tasks/{taskId}`
        Where `{base_url}` is replaced by `http::loacalhost:3000`
        Replace `taskId` with the unique ID of the task to update. Example: `5`. When creating tasks, the service assigns `id` values sequentially.
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        You can change the values of each property as you'd like.

        ```js
        {
            "user_id": 3,
            "title": "Get new tires",
            "description": "Get new tires for Hoppity",
            "due_date": "2025-03-11T14:00",
            "warning": "-60"
        }
        ```

1. In the Postman app, select **Send** to make the request.
1. Watch for the response body, which should look something like this. Note that the names should be the same as you used in your **Request body** and the response should include the new user's `id`.

    ```js
    {
        "user_id": 3,
        "title": "Get new tires",
        "description": "Get new tires for Hoppity",
        "due_date": "2025-03-11T14:00",
        "warning": "-60",
        "id": 5
    }
    ```

After doing this tutorial in Postman, you might like to repeat it in
your favorite programming language. To do this, adapt the values from
the tutorial to the properties and arguments that the language uses to
make REST API calls.

Here is an example request in cURL:

```curl -X PUT \
  http://localhost:3000/tasks/5 \
  -H "Content-Type: application/json" \
  -d '{
    "user_id": 3,
    "title": "Get new tires",
    "description": "Get new tires for Hoppity",
    "due_date": "2025-03-11T14:00",
    "warning": "-60"
  }'
  ```

## Error Responses

* `400 Bad Request`:
    * Malformed JSON.
    * The `id` in body doesn't match the `taskId` in path.
    * Invalid date format.
* `404 Not Found`: No task exists with the provided taskId.
