# Delete task by ID

Removes a [`task`](task.md) object specified by the `id` parameter.

## Request URL

**Method**: `DELETE`

**URL**: `{{base_url}}/tasks/{taskId}`

## Parameters

| Name | Variable |
| ---- | ---------|
| taskId | integer |

## Headers

**Content-Type:** `application/json`

## Request body

N/A

## Response body

`
{}
`

## Responses
* 200: Successful
* 404: Task object not found
* ECONNREFUSED: To-Do Service is offline
