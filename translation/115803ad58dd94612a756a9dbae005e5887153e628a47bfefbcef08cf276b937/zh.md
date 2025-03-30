```
Vector{T}(undef, n)
```

构造一个长度为 `n` 的未初始化 [`Vector{T}`](@ref)。

# 示例

```julia-repl
julia> Vector{Float64}(undef, 3)
3-element Array{Float64, 1}:
 6.90966e-310
 6.90966e-310
 6.90966e-310
```
