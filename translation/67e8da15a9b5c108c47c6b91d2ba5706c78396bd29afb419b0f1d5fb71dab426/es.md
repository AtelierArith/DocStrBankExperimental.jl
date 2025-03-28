```
myid()
```

Obtiene el id del proceso actual.

# Ejemplos

```julia-repl
julia> myid()
1

julia> remotecall_fetch(() -> myid(), 4)
4
```
