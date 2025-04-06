```
lyap(A, C)
```

计算连续李雅普诺夫方程 `AX + XA' + C = 0` 的解 `X`，其中 `A` 的特征值没有零实部，并且没有两个特征值是负的共轭复数。

# 示例

```jldoctest
julia> A = [3. 4.; 5. 6]
2×2 Matrix{Float64}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Matrix{Float64}:
 1.0  1.0
 1.0  2.0

julia> X = lyap(A, B)
2×2 Matrix{Float64}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' ≈ -B
true
```
