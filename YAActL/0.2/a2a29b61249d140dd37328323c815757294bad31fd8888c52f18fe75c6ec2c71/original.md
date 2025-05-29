```
init!(lk::Link, f::Function, args...; kwargs...)
init!(name::Symbol, ....)
```

Tell an actor `lk` to save the function `f` with the given  arguments as an [`init`](@ref _ACT) function, to execute it  and to save the returned value as state [`sta`](@ref _ACT)  variable.

The `init` function will be called at actor restart.

!!! note "This behavior is not yet implemented!"
    It is needed for supervision.

