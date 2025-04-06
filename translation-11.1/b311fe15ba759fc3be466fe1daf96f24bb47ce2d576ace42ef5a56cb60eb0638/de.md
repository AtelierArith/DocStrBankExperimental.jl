```
@fetch expr
```

Entspricht `fetch(@spawnat :any expr)`. Siehe [`fetch`](@ref) und [`@spawnat`](@ref).

# Beispiele

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
