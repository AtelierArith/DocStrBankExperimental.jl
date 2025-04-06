```
\(x, y)
```

左除法运算符：将 `y` 乘以 `x` 的逆矩阵，结果在左侧。对于整数参数，返回浮点结果。

# 示例

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
