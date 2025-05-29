```
diaghessian(f, args...) -> Tuple
```

ヘッセ行列の対角部分。各引数 `x` に対して、同じ形状の `h` を含むタプルを返します。ここで `h[i] = Hᵢᵢ = ∂²y/∂x[i]∂x[i]` です。元の評価 `y = f(args...)` は実数 `y` を返さなければなりません。

ベクトル引数 `x` の場合、これは `(diag(hessian(f,x)),)` と同等です。 [`hessian`](@ref) と同様に、Zygote の上で ForwardDiff を使用します。

!!! warning
    `Number` および `AbstractArray` 以外の任意の型の引数に対して、結果は `nothing` です。


# 例

```jldoctest; setup=:(using Zygote, LinearAlgebra)
julia> diaghessian(x -> sum(x.^3), [1 2; 3 4])[1]
2×2 Matrix{Int64}:
  6  12
 18  24

julia> Diagonal(vec(ans)) == hessian(x -> sum(x.^3), [1 2; 3 4])  # フルヘッセ行列は対角
true

julia> diaghessian((x,y) -> sum(x .* y .* y'), [1 22; 333 4], [0.5, 0.666])  # 2つの配列引数
([0.0 0.0; 0.0 0.0], [2.0, 8.0])

julia> diaghessian(atan, 1, 2)  # 2つのスカラー引数
(-0.16, 0.16)

julia> hessian(xy -> atan(xy[1], xy[2]), [1, 2])  # フルヘッセ行列は対角ではない
2×2 Matrix{Float64}:
 -0.16  -0.12
 -0.12   0.16
```
