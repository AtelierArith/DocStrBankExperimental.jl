```
nworkers()
```

Obtenez le nombre de processus de travail disponibles. Cela est un de moins que [`nprocs()`](@ref). Égal à `nprocs()` si `nprocs() == 1`.

# Exemples

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
