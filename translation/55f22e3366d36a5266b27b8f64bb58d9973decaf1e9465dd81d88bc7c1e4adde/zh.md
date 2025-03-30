```
schur!(A) -> F::Schur
```

与 [`schur`](@ref) 相同，但使用输入参数 `A` 作为工作空间。

# 示例

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 矩阵{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur!(A)
Schur{Float64, 矩阵{Float64}, 向量{Float64}}
T 因子:
2×2 矩阵{Float64}:
 3.0   9.0
 0.0  -2.0
Z 因子:
2×2 矩阵{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
特征值:
2 元素 向量{Float64}:
  3.0
 -2.0

julia> A
2×2 矩阵{Float64}:
 3.0   9.0
 0.0  -2.0
```
