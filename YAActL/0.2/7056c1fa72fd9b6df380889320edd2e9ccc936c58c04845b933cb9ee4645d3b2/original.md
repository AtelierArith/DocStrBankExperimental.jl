```
exit!(lk::Link, code=0)
exit!(name::Symbol, code=0)
```

Tell an actor `lk` (or `name` if registered) to exit. If it has a [`term`](@ref _ACT)  function, it calls it with `code` as last argument. 

!!! note "This behavior is not yet fully implemented!"
    It is needed for supervision.

