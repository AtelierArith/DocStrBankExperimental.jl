```
randperm([rng=default_rng(),] n::Integer)
```

長さ `n` のランダムな順列を構築します。オプションの `rng` 引数は乱数生成器を指定します（[乱数](@ref)を参照）。結果の要素型は `n` の型と同じです。

任意のベクトルをランダムに並べ替えるには、[`shuffle`](@ref) または [`shuffle!`](@ref) を参照してください。

!!! compat "Julia 1.1"
    Julia 1.1 では `randperm` は `eltype(v) == typeof(n)` のベクトル `v` を返しますが、Julia 1.0 では `eltype(v) == Int` です。


# 例

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
