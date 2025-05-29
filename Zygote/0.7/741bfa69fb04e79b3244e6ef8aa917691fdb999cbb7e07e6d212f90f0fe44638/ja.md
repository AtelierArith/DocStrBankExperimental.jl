```
jacobian(loss, ::Params)
```

暗黙のパラメータを持つ[`gradient`](@ref)と同様に、このメソッドはゼロ引数の関数を受け取り、各パラメータのヤコビ行列を含む`IdDict`のようなオブジェクトを返します。

# 例

```jldoctest; setup=:(using Zygote)
julia> xs = [1 2; 3 4]; ys = [5,7,9];

julia> Jxy = jacobian(() -> ys[1:2] .+ sum(xs.^2), Params([xs, ys]))
Grads(...)

julia> Jxy[ys]
2×3 Matrix{Int64}:
 1  0  0
 0  1  0

julia> Jxy[xs]
2×4 Matrix{Int64}:
 2  6  4  8
 2  6  4  8
```
