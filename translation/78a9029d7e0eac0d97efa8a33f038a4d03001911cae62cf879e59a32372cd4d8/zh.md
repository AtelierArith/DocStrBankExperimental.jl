```
factorize(A)
```

计算 `A` 的一个方便的分解，基于输入矩阵的类型。`factorize` 检查 `A` 以确定它是否是对称/三角形等，如果 `A` 作为通用矩阵传递。`factorize` 检查 `A` 的每个元素以验证/排除每个属性。它会在能够排除对称性/三角形结构时立即短路。返回值可以重复使用，以高效地解决多个系统。例如：`A=factorize(A); x=A\b; y=A\C`。

| `A` 的属性 | 分解类型                                     |
|:------- |:---------------------------------------- |
| 正定      | Cholesky (见 [`cholesky`](@ref))          |
| 密集对称/厄米 | Bunch-Kaufman (见 [`bunchkaufman`](@ref)) |
| 稀疏对称/厄米 | LDLt (见 [`ldlt`](@ref))                  |
| 三角形     | 三角形                                      |
| 对角形     | 对角形                                      |
| 双对角     | 双对角                                      |
| 三对角     | LU (见 [`lu`](@ref))                      |
| 对称实三对角  | LDLt (见 [`ldlt`](@ref))                  |
| 一般方形    | LU (见 [`lu`](@ref))                      |
| 一般非方形   | QR (见 [`qr`](@ref))                      |

例如，如果在一个厄米正定矩阵上调用 `factorize`，那么 `factorize` 将返回一个 Cholesky 分解。

# 示例

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factorize(A) # factorize 将检查 A 是否已经被分解
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

这返回一个 `5×5 Bidiagonal{Float64}`，现在可以传递给其他线性代数函数（例如特征求解器），这些函数将使用针对 `Bidiagonal` 类型的专门方法。
