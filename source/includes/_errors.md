# Errors

The TIPU API uses the following error codes:

| Error Code | Meaning                                                                                    |
| ---------- | ------------------------------------------------------------------------------------------ |
| 401        | Unauthorized -- Your JWT is expired, signed with the wrong key or missing.                 |
| 403        | Forbidden -- The grant you requested doesn't belong to the encoded organisation in the JWT |
| 404        | Not Found -- The specified grant could not be found.                                       |
| 500        | Internal Server Error -- We had a problem with our server. Try again later.                |
| 503        | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.  |
