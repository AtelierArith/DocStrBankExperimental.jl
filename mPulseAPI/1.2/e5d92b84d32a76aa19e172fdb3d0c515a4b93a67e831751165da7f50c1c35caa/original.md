Thrown when the REST API has an internal server error and returns a `500 Internal Server Error`

### Fields

`msg::AbstractString` :    The string "Internal Server Error, please report this. Timestamp: <current unix timestamp in seconds since the epoch>"

`response::Response` :    The response object from the REST API call.  You can inspect headers, data, cookies, redirects, and the initiating request.

`responseBody::AbstractString` :    The body of the HTTP response from the server
