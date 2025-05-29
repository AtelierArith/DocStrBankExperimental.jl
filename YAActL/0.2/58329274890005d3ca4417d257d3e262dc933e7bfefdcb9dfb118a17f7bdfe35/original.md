```
become(bhv::Function, args...; kwargs...)
```

Cause your actor to take on a new behavior. This can only be called from inside an actor/behavior.

# Arguments

  * `bhv::Function`: function implementing the new behavior,
  * `args...`: arguments to `bhv` (without `msg`),
  * `kwargs...`: keyword arguments to `bhv`.
