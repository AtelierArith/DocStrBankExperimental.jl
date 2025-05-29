```
term!(lk::Link, f::Function, args1...; kwargs...)
term!(name::Symbol, ....)
```

Tell an actor `lk` to execute a function `f` with the given arguments when it terminates. `f` must accept a `code=0`  as last argument. This is added by the actor to `args1...`  when it [`exit!`](@ref)s.

!!! note "This behavior is not yet implemented!"
    It is needed for supervision.

