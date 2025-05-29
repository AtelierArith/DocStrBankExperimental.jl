Thrown when the token used to authenticate with the REST API is invalid or has expired

### Fields

`msg::AbstractString` :    This message is always set to "Error Authenticating with REST API"

`response::Response` :    The response object from the REST API call.  You can inspect headers, data, cookies, redirects, and the initiating request.

`responseBody::AbstractString` :    The body of the HTTP response from the server
