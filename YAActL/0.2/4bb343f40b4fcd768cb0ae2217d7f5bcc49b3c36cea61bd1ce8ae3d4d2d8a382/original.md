```
become!(lk::Link, bhv::Function, args1...; kwargs...)
become!(name::Symbol, ....)
```

Cause an actor to change behavior.

# Arguments

  * actor `lk::Link` (or `name::Symbol` if registered),
  * `bhv`: function implementing the new behavior,
  * `args1...`: first arguments to `bhv` (without a possible `msg` argument),
  * `kwargs...`: keyword arguments to `bhv`.
