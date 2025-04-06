```
@fetchfrom
```

相当于 `fetch(@spawnat p expr)`。请参见 [`fetch`](@ref) 和 [`@spawnat`](@ref)。

# 示例

```julia-repl
julia> addprocs(3);

julia> @fetchfrom 2 myid()
2

julia> @fetchfrom 4 myid()
4
```
