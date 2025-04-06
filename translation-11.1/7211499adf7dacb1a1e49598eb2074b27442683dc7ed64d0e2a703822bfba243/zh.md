```
clamp(x, T)::T
```

将 `x` 限制在 `typemin(T)` 和 `typemax(T)` 之间，并将结果转换为类型 `T`。

另见 [`trunc`](@ref)。

# 示例

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```
