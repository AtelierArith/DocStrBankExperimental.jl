```
nworkers()
```

Holen Sie die Anzahl der verfügbaren Arbeitsprozesse. Dies ist eins weniger als [`nprocs()`](@ref). Gleich `nprocs()`, wenn `nprocs() == 1`.

# Beispiele

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
