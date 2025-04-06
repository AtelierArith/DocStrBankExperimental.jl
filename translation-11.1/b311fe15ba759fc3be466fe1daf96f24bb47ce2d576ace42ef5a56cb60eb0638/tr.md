```
@fetch expr
```

`fetch(@spawnat :any expr)` ile eşdeğerdir. [`fetch`](@ref) ve [`@spawnat`](@ref) bakınız.

# Örnekler

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
