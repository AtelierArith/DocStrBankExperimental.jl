```
procs()
```

Devuelve una lista de todos los identificadores de proceso, incluyendo el pid 1 (que no está incluido por [`workers()`](@ref)).

# Ejemplos

```julia-repl
$ julia -p 2

julia> procs()
3-element Array{Int64,1}:
 1
 2
 3
```
