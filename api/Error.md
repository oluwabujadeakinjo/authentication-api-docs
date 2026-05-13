### Error Messages

#### Invalid Password (401 Unauthorized)

```json
{
    "status": "401",
    "error": "invalid_credentials",
    "message": "Invalid credentials. Verify your username and password"
}
```

#### Missing Field (400 Bad Request)

```json
{
    "status": "400",
    "error": "missing_field",
    "message": "A required firld is missing. Ensure all required fields are present"
}
```

#### Expired Token (401 Unauthorized)

```json
{
    "status": "401",
    "error": "token_expired",
    "message": "Access token expired. Generate new token"
}
```

#### Unauthorized Access (403 Forbidden)

```json
{
    "status": "403",
    "error": "forbidden",
    "message": "You do not have permission to access this resource."
}
```
#### Server Error (500 Internal Server Error)

```json
{
    "status": "500",
    "error": "server_error",
    "message": "An internal error occured. Please try again later."
}
```

### Error Handling
