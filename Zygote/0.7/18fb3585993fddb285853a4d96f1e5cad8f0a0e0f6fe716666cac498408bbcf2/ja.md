```
hessian(f, x)
```

ヘッセ行列 `∂²f/∂x²` を構築します。ここで `x` は実数または配列であり、`f(x)` は実数です。`x` が配列の場合、結果は行列 `H[i,j] = ∂²f/∂x[i]∂x[j]` となり、引数が高次元であっても線形インデックス `x[i]` を使用します。

これは、`hessian_dual(f, x)` を呼び出す際に、逆ではなく順方向、ZygoteではなくForwardDiffを使用します。全てZygoteの代替として [`hessian_reverse`](@ref) を参照してください。

対角部分のみを計算するには、[`diaghessian`](@ref) も参照してください。

# 例

```jldoctest; setup=:(using Zygote)
julia> hessian(x -> x[1]*x[2], randn(2))
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> hessian(x -> sum(x.^3), [1 2; 3 4])  # xの線形インデックスを使用
4×4 Matrix{Int64}:
 6   0   0   0
 0  18   0   0
 0   0  12   0
 0   0   0  24

julia> hessian(sin, pi/2)
-1.0
```
