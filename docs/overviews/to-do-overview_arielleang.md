# To-Do Service: API documentation for a lightweight task reminder service

Welcome to the REST API of **To-Do**, a simple and efficient service where you can create tasks and task reminders.

Use this API to learn how to install the service in your system, enroll new users, create and update tasks, and set up reminders.

|                 |  **Quick links**  |           |
|-----------------|:-------------:|-----------|
| [Install service](../before-you-start-a-tutorial.md) | [Tutorials](#tutorials) | [API Reference](#api-reference) |

---

## Get started

> Have you [installed the To-Do Service](../before-you-start-a-tutorial.md) in your development system? Make sure you have all the requirements in your system before you begin.

Start with a quick tutorial on enrolling a user. Since the **To-Do** Service requires a user to create a task, this tutorial serves as a good jumping-off point to learn how to use the API.

Enrolling a new user in the service requires that you use the `POST` method to store the details of a new [`user`](../api/user.md) resource in the service.

**To enroll a new user:**

1. Start the service by using this command in your command-line tool.

    ```shell
    cd <your-github-workspace>/to-do-service/api
    json-server -w to-do-db-source.json
    ```

2. Open the Postman app on your desktop.
3. In the Postman app, create a new request with these values:
    * **METHOD**: POST
    * **URL**: `{{base_url}}/users`
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        You can change the values of each property as you'd like.

        ```js
        {
            "last_name": "Jones",
            "first_name": "Jenny",
            "email": "jen.jones@example.com"
        }
        ```

4. In the Postman app, choose **Send** to make the request.
5. The response body should look something like this. Note that the names should be the same as you used in your **Request body** and the response should include the new user's `id`.

    ```js
    {
        "last_name": "Jones",
        "first_name": "Jenny",
        "email": "jen.jones@example.com",
        "id": 5
    }
    ```

---

## Tutorials

Now that you've successfully [enrolled your first user](#get-started), you can take a look at tutorials for more operations in the service:

* [Create a new task](../tutorials/add-a-new-task.md)
* [Retrieve a list of users](../api/users-get-all-users.md)
* [Retrieve users by their user ID](../api/users-get-user-by-id.md)

---

## API reference

> The `{base_url}` value of the resources depends on the installation of the service.
>
> When run locally for testing, the `{base_url}` is generally `http://localhost:3000`.

### Resources for the To-Do Service

* [user](../api/user.md)
* [task](../api/task.md)
