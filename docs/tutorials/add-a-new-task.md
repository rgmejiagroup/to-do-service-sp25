---
layout: page
---

# Tutorial: Add a new task

In this tutorial you'll learn you how to
add a new [`task`](../api/task.md) in the To-Do Service API.

The tutorial should take about 10 minutes to complete.

## Before you start

Make sure you've completed [Before you start a tutorial](../before-you-start-a-tutorial.md) and set up your development system.  

When you finish setting up your development system, you should have the server running locally at `http://localhost:3000`. To check that it's running, or to restart it after ending a session, use this command:

```shell
cd <your-github-workspace>/to-do-service/api
    json-server -w to-do-db-source.json
```

If your server is running, you'll see this:

```text
Type s + enter at any time to create a snapshot of the database
Watching...
```

## Add a new task

Use the `POST` method to add a task in the To-Do Service. Here's how to send the request with both Postman and cURL.

### Using Postman

In the Postman desktop app, navigate to **Create a New API Request** and select **New Request**. Give the new request the following values.

* **METHOD**: POST
* **URL**: `{base_url}/tasks`
* **Headers**:
    * `Content-Type: application/json`  
* **Request Body**:

```json
    {
        "user_id": 3,
        "title": "Get new tires",
        "description": "Get new tires for Hoppity",
        "due_date": "2025-03-11T14:00",
        "warning": "-60"
    }
```

Change the JSON values to fit your new task, and click **Send**.

### Using cURL

If you'd rather use cURL in command line, here's what the same request looks like.

```shell
curl -X POST "{base_url}/tasks" -H "Content-Type: application/json" -d "{\"user_id\": 3, \"title\": \"Get new tires\", \"description\": \"Get new tires for Hoppity\", \"due_date\": \"2025-03-11T14:00\", \"warning\": \"-60\"}"
```

## Example response

Whether you use Postman or cURL, if the request is successful, you'll get a JSON response that looks like this:

```json
    {
        "user_id": 3,
        "title": "Get new tires",
        "description": "Get new tires for Hoppity",
        "due_date": "2025-03-11T14:00",
        "warning": "-60",
        "id": 5
    }
```

This response is the same as the body of the request, except that it includes an `id` property, which contains the unique identifier of the task resource you just created. You can now retrieve the new task by sending a `GET` request to `/tasks/{id}`. Here's what that request looks like in Postman:

```text
GET http://localhost:3000/tasks/5
```

And in cURL:

```shell
curl http://localhost:3000/tasks/5
```

The JSON response returned is the same as the one returned by the `POST` request.

## Troubleshooting

Here are a couple of errors your might run into.

* `404: Not Found` most likely means an error in the URL. Try checking and re-entering it.

* `Could not send request` means the local server isn't running and needs to restart.

## Next steps

Now that you can add tasks, learn how to [enroll a new user](https://uwc2-apidoc.github.io/to-do-service-sp25/tutorials/enroll-a-new-user.html).
