```
norm(x::Number, p::Real=2)
```

对于数字，返回 $\left( |x|^p \right)^{1/p}$。

# 示例

```jldoctest
julia> norm(2, 1)
2.0

julia> norm(-2, 1)
2.0

julia> norm(2, 2)
2.0

julia> norm(-2, 2)
2.0

julia> norm(2, Inf)
2.0

julia> norm(-2, Inf)
2.0
```
