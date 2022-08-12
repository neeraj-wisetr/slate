# Errors

There are 7 types of errors in Autonami Public API:


Error Code | Error Type
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Request rejected by the server
404 | Not Found -- Data not found
405 | Method Not Allowed -- You tried to access the data with an invalid method.
406 | Wrong Format -- You requested a format that isn't json.
422 | Unprocessable Entity -- The request failed the validation
500 | Internal Server Error -- We had a problem with our server. Try again later.
