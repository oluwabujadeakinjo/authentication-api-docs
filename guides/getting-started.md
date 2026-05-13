# Getting Started with the Authentication API

This guide shows how to authenticate users and use the API. By the end you will be able to send requests and handle responses.

## Prerequisites

You need:
- Basic knowledge of HTTP APIs
- An HTTP client
- API base URL

## Step 1: Make a Login Request

### Endpoint

`POST /auth/login`

### Request Example

```json
{
    "username": "isaac_timothy",
    "password": "strong_password",
    "client_id": "id_5348"
}
```
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

## Step 2: Understand the Response 

The response contains:
* `access_token`: a short-lived token that is included in subsequent requests.
* `expires_in`: the lifespan of the access token. It is written in seconds.
* `user_id`: a unique identifier assigned to the user.

## Step 3: Use the Token

Include the **access token** in the subsequent requests:
`Authorization: Bearer <access_token>`

### Request using token

```bash
curl -X GET https://api.example.com/v1/auth/login \
-H "Authorization: Bearer <access_token>" 
```

## Error Handling

The table below shows common errors:
|**Status**|**Error**|**Message**|
|----------|---------|-----------|
|`401 Unauthorized`|`invalid_credentials`|Invalid credentials. Verify username and password, and try again.|
|`401 Unauthorized`|`token_expired`|The access token has expired. Generate a new token.|
|`500 Internal Server Error`|`server_error`|An internal server error occurred. Please try again later.|

## Next Steps

- Refer to the [API documentation](./Getting%20Started.md) for detailed endpoint specifications
- Review [error handling](https://github.com/oluwabujadeakinjo/authentication-api-docs/blob/main/api/Error.md) documentation to understand possible responses
