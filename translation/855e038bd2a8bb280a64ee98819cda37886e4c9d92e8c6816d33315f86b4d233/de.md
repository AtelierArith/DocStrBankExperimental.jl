```
@fetchfrom
```

Entspricht `fetch(@spawnat p expr)`. Siehe [`fetch`](@ref) und [`@spawnat`](@ref).

# Beispiele

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
