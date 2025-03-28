```
@fetch expr
```

Equivalente a `fetch(@spawnat :any expr)`. Ver [`fetch`](@ref) y [`@spawnat`](@ref).

# Ejemplos

```julia-repl
julia> addprocs(3);

julia> @fetch myid()
2

julia> @fetch myid()
3

julia> @fetch myid()
4

julia> @fetch myid()
2
```
