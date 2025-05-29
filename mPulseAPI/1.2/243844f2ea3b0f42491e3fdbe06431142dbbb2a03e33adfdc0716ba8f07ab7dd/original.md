Thrown when the REST API has a problem and returns something other than a 2xx response.

### Fields

`msg::AbstractString` :    The error message

`response::Response` :    The response object from the REST API call.  You can inspect headers, data, cookies, redirects, and the initiating request.

`responseBody::AbstractString` :    The body of the HTTP response from the server
