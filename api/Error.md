# Error handling

## Error status code summary
Use this table for a quick reference for HTTP status codes and their associated error types:

|**Status code**|**Error type**|**Description**|**Solution**|
|----------|---------|-----------|----------|
|`401 Unauthorized`|`invalid credentials`|Authentication failed|Verify username and password, then try again.|
|`401 Unauthorized`|`token_expired`|Session timeout|The access token has expired. Generate a new token to continue|
|`500 Internal Server Error`|`server_error`|Internal fault|An unexpected error occurred. Please try again later.|

## Error details

### Invalid password (401 Unauthorized)
Returned when the username or password does not match system records.

```json
{
    "status": 401,
    "error": "invalid_credentials",
    "message": "Invalid credentials. Verify your username and password"
}
```

### Missing field (400 Bad Request)
Returned when a required property is absent from the request body payload.

```json
{
    "status": 400,
    "error": "missing_field",
    "message": "A required firld is missing. Ensure all required fields are present"
}
```

### Expired token (401 Unauthorized)
Returned when the provided access token has passed its one-hour lifetime limit.

```json
{
    "status": 401,
    "error": "token_expired",
    "message": "Access token expired. Generate new token"
}
```

### Unauthorized access (403 Forbidden)
Returned when the credentials are valid, but the user account does not have authorization to access the specific resource.

```json
{
    "status": 403,
    "error": "forbidden",
    "message": "You do not have permission to access this resource."
}
```
### Server error (500 Internal Server Error)
Returned when an internal issue occurs on the hosting environment.

```json
{
    "status": 500,
    "error": "server_error",
    "message": "An internal error occured. Please try again later."
}
```


