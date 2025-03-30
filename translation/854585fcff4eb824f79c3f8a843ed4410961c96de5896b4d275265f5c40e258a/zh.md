```
(I::UniformScaling)(n::Integer)
```

从 `UniformScaling` 构造一个 `Diagonal` 矩阵。

!!! compat "Julia 1.2"
    此方法自 Julia 1.2 起可用。


# 示例

```jldoctest
julia> I(3)
3×3 Diagonal{Bool, Vector{Bool}}:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1

julia> (0.7*I)(3)
3×3 Diagonal{Float64, Vector{Float64}}:
 0.7   ⋅    ⋅
  ⋅   0.7   ⋅
  ⋅    ⋅   0.7
```
