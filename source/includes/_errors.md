# Errors

There are 7 types of errors in FunnelKit Automations Public API:

Error Code | Error Type
---------- | -------
400 | Bad Request -- Your request is invalid
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- Request rejected by the server
404 | Not Found -- Data not found
405 | Method Not Allowed -- You tried to access the data with an invalid method
406 | Wrong Format -- You requested a format that isn't json
422 | Unprocessable Entity -- The request failed the validation
500 | Internal Server Error -- We had a problem with our server. Try again later

> JSON error response example:

```json
{
  "code": "api_key_missing",
  "message": "API key is missing."
}
```

```json
{
  "code": "api_key_invalid",
  "message": "API key is not valid."
}
```

```json
{
  "code": "permission_denied",
  "message": "API key does not have this permission."
}
```

```json
{
  "code": "api_key_inactive",
  "message": "API key is not active."
}
```

```json
{
  "code": "data_not_found",
  "message": "Data not found."
}
```

```json
{
  "code": "required_fields_missing",
  "message": "Some arguments are required which are missing"
}
```

```json
{
  "code": "email_invalid",
  "message": "Contact Email Address is not valid."
}
```

```json
{
  "code": "already_exists",
  "message": "Already exists in the system."
}
```

```json
{
  "code": "contact_not_exists",
  "message": "Contact not exists."
}
```

```json
{
  "code": "unprocessable_entity",
  "message": "The request failed validation or was not allowed for another reason."
}
```

```json
{
  "code": "unknown_error",
  "message": "Some error occurred."
}
```

```json
{
  "code": "already_exists",
  "message": "Already exists in the system."
}
```

```json
{
  "code": "method_not_allowed",
  "message": "Method not allowed."
}
```
