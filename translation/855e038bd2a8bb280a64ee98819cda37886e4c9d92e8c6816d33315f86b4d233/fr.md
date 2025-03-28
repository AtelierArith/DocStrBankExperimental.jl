```
@fetchfrom
```

Équivalent à `fetch(@spawnat p expr)`. Voir [`fetch`](@ref) et [`@spawnat`](@ref).

# Exemples

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
