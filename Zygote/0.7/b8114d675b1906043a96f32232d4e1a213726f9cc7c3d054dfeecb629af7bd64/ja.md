```
jacobian(f, args...) -> Tuple
```

各配列 `a ∈ args` に対して、これは `Ja[k,i] = ∂y[k]/∂a[i]` を持つ行列を返します。ここで `y = f(args...)` は通常ベクトルです。高次元の配列は `vec(a)` または出力のための `vec(y)` のように扱われます。

スカラー `x::Number ∈ args` の場合、結果はベクトル `Jx[k] = ∂y[k]/∂x` となり、スカラー `y` の場合、すべての結果は1行のみになります。

他の引数タイプの場合、[`gradient`](@ref) が機能する場合でも、結果は生成されません。

この逆モードのヤコビ行列は、`y` の各要素に対してプルバックを一度評価する必要があります。通常、`length(y)` が `length(a)` に比べて小さい場合にのみ効率的です。そうでない場合、順方向モードの方が良い可能性があります。

他に [`withjacobian`](@ref)、[`hessian`](@ref)、[`hessian_reverse`](@ref) も参照してください。

# 例

```jldoctest; setup=:(using Zygote)
julia> jacobian(a -> 100*a[1:3].^2, 1:7)[1]  # 最初のインデックス（行）は出力
3×7 Matrix{Int64}:
 200    0    0  0  0  0  0
   0  400    0  0  0  0  0
   0    0  600  0  0  0  0

julia> jacobian((a,x) -> a.^2 .* x, [1,2,3], 1)  # スカラー引数はベクトルヤコビ行列を持つ
([2 0 0; 0 4 0; 0 0 6], [1, 4, 9])

julia> jacobian((a,d) -> prod(a, dims=d), [1 2; 3 4; 5 6], 2)
([2 0 … 0 0; 0 4 … 3 0; 0 0 … 0 5], [0, 0, 0])
```

!!! warning
    `Number` および `AbstractArray` 以外の型の引数の場合、結果は `nothing` です。


```
julia> jacobian((a,s) -> a.^length(s), [1,2,3], "str")
([3 0 0; 0 12 0; 0 0 27], nothing)

julia> jacobian((a,t) -> sum(a .* t[1]) + t[2], [1,2,3], (4,5))
([4 4 4], nothing)

julia> gradient((a,t) -> sum(a .* t[1]) + t[2], [1,2,3], (4,5))  # gradient はタプルを理解する
([4 4 4], (6, 1))
```
