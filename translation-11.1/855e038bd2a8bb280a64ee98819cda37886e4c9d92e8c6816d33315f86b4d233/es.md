```
@fetchfrom
```

Equivalente a `fetch(@spawnat p expr)`. Ver [`fetch`](@ref) y [`@spawnat`](@ref).

# Ejemplos

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
