# Getting started with the Authentication API

Learn how to authenticate users and generate access tokens using the Authentication API. By the end of this guide, you will be able to successfully request a token and use it to access protected endpoints.

## Prerequisites

Before you begin, ensure you have:
- Basic knowledge of REST APIs and HTTP methods.
- An command-line tool like `curl` (or an API platform like Postman).
- The API base URL: `https://api.example.com/v1`.

## Authentication flow

1. **Client sends credentials**: The client sends a request including their **username** and **password.**

2. **Server validates**: The server authenticates the request and sends a response:
     - If the credentials are valid, it sends a `200 OK` status code and grants the user access.
     - If the credentials are invalid, it sends a `401 Unauthorized` status code and an error message.

3. **Token is returned**: If the credentials are valid, the server returns a short-lived **access token** in its response.

4. **Token is used in future requests**: The token is included in the client's subsequent requests.

## Step 1: Make a login request
To generate a token, send a `POST` request to the `/auth/login` endpoint with your user credentials.

Send the request using cURL:

```bash
curl -X POST https://api.example.com/v1/auth/login \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-d '{
    "username": "isaac_timothy",
    "password": "strong_password",
    "client_id": "id_5348"
}'
```

## Step 2: Understand the response 
If your credentials are valid, the server returns a `200 OK` status and a JSON payload containing your token:

```JSON
{
     "access_token": "tgF65fcjIo9Hddftty8Y7p...",
     "expires_in": 3600,
     "user_id": "u_5348"
}
```

* `access_token`: The secure string used to authorize subsequent requests.
* `expires_in`: The lifespan of the access token in seconds (3600 seconds=1 hour).
* `user_id`: The unique identifier for the authenticated user.

## Step 3: Use the Token
Once you have the `access_token`, include it in the `Authorization` header of all future requests to access protected resources.

**Format:** `Authorization: Bearer <access_token>`

**Example request to a protected endpoint**

```bash
curl -X GET https://api.example.com/v1/auth/login \
-H "Authorization: Bearer <access_token>" 
```

## Troubleshooting common errors
If your request fails, the API returns a standard HTTP status code and an error message.

The table below shows common errors:
|**Status**|**Error**|**Resolution**|
|----------|---------|-----------|
|`401 Unauthorized`|`invalid_credentials`|Verify username and password, and try again.|
|`401 Unauthorized`|`token_expired`|The access token has expired. Generate a new token.|
|`500 Internal Server Error`|`server_error`|The server encountered an issue. Wait a moment and try again.|

## Next steps

- Review the [**Authentication API reference**](./Getting%20Started.md) for detailed parameter specifications.
- Read the full [**Error handling guide**](https://github.com/oluwabujadeakinjo/authentication-api-docs/blob/main/api/Error.md) to understand all potential API responses.
