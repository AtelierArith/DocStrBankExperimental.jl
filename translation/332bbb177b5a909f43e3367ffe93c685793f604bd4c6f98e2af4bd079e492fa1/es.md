```
nworkers()
```

Obtiene el número de procesos de trabajo disponibles. Esto es uno menos que [`nprocs()`](@ref). Igual a `nprocs()` si `nprocs() == 1`.

# Ejemplos

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
