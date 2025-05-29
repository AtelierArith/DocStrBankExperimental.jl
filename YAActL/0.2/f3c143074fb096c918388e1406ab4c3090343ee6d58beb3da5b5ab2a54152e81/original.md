```
request!(lk::Link, msg::Message; full=false, timeout::Real=5.0)
request!(lk::Link, Msg::Type{<:Message}, args...; kwargs...)
request!(name::Symbol, args...; kwargs...)
```

Send a message to an actor, block, receive and return the result.

# Arguments

  * `lk::Link`: actor link, or `name::Symbol` (if registered),
  * `msg::Message`: a message,
  * `Msg::Type{<:Message}`: a message type,
  * `args...`: optional arguments to `Msg`,
  * `full`: if `true` return the full [`Response`](@ref) message.
  * `timeout::Real=5.0`: timeout in seconds after which a    [`Timeout`](@ref) is returned,
  * `kwargs...`: `full` or `timeout`.
