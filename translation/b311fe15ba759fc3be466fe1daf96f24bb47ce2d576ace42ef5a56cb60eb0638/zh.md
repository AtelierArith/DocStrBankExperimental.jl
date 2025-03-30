```
@fetch expr
```

等同于 `fetch(@spawnat :any expr)`。请参见 [`fetch`](@ref) 和 [`@spawnat`](@ref)。

# 示例

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
