```
LinkParams(pid=myid(), size=32; taskref=nothing, spawn=false)
```

Parameters for setting up an [`Actor`](@ref). 

  * `pid::Int`: process identification,
  * `size::Int`: channel buffer size, must be `size ≥ 10`,
  * `taskref::Union{Nothing, Ref{Task}}`: If you need a reference to the created task,   pass a `Ref{Task}` object via the keyword argument `taskref`.
  * `spawn::Bool`: If spawn = true, the Task created may be scheduled on another   thread in parallel, equivalent to creating a task via `Threads.@spawn`.
