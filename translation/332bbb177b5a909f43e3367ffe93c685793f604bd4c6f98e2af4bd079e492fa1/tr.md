```
nworkers()
```

Mevcut işçi süreçlerinin sayısını alır. Bu, [`nprocs()`](@ref) değerinden bir eksiktir. `nprocs() == 1` ise `nprocs()` ile eşittir.

# Örnekler

```julia-repl
$ julia -p 2

julia> nprocs()
3

julia> nworkers()
2
```
