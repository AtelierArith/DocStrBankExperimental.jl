```
hessenberg(A) -> Hessenberg
```

计算 `A` 的 Hessenberg 分解并返回一个 `Hessenberg` 对象。如果 `F` 是因式分解对象，则可以通过 `F.Q`（类型为 `LinearAlgebra.HessenbergQ`）访问单位矩阵，通过 `F.H`（类型为 [`UpperHessenberg`](@ref)）访问 Hessenberg 矩阵，任一矩阵都可以通过 `Matrix(F.H)` 或 `Matrix(F.Q)` 转换为常规矩阵。

如果 `A` 是 [`Hermitian`](@ref) 或实 [`Symmetric`](@ref)，则 Hessenberg 分解会产生一个实对称三对角矩阵，`F.H` 的类型为 [`SymTridiagonal`](@ref)。

请注意， shifted factorization `A+μI = Q (H+μI) Q'` 可以通过 `F + μ*I` 使用 [`UniformScaling`](@ref) 对象 [`I`](@ref) 高效构造，该对象创建一个具有共享存储和修改过的移位的新 `Hessenberg` 对象。给定 `F` 的移位可以通过 `F.μ` 获得。这是有用的，因为一旦创建了 `F`，可以高效地执行多个移位求解 `(F + μ*I) \ b`（对于不同的 `μ` 和/或 `b`）。

迭代分解会产生因子 `F.Q, F.H, F.μ`。

# 示例

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q factor: 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H factor:
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # 通过迭代解构

julia> q == F.Q && h == F.H
true
```
