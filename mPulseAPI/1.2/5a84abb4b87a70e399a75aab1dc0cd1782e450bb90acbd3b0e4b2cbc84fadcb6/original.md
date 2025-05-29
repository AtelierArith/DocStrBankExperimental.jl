Thrown when a request parameter is invalid

### Fields

`msg::AbstractString` :    The error message sent from the mPulse server

`code::AbstractString` :    The error code sent from the mPulse server

`parameter::AbstractString` :    The parameter that the mPulse server had a problem with

`value::AbstractString` :    The value of the parameter that the mPulse server had a problem with

`response::Response` :    The response object from the REST API call.  You can inspect headers, data, cookies, redirects, and the initiating request.
