```
@fetch expr
```

Équivalent à `fetch(@spawnat :any expr)`. Voir [`fetch`](@ref) et [`@spawnat`](@ref).

# Exemples

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
