```
exec!(lk::Link, from::Link, f::Function, args...; kwargs...)
exec!(lk::Link, from::Link, fu::Func)
exec!(lk::Link, fu::Func; timeout::Real=5.0)
exec!(name::Symbol, ....)
```

Ask an actor `lk` (or `name` if registered) to execute an  arbitrary function and to send the returned value as  [`Response`](@ref).

# Arguments

  * `lk::Link` or `name::Symbol` of the actor,
  * `from::Link`: the link a `Response` should be sent to.   If `from` is ommitted, `exec!` blocks, waits and returns    the result. In that case there is a `timeout`.
  * `f::Function, args...; kwargs...` or
  * `fu::Func`: function arguments,
  * `timeout::Real=5.0`: timeout in seconds. Set `timeout=Inf`    if you don't want a timeout.
