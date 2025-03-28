```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

[`eigvals`](@ref)と同様ですが、コピーを作成するのではなく、入力`A`を上書きすることでスペースを節約します。`permute`、`scale`、および`sortby`のキーワードは[`eigen`](@ref)と同じです。

!!! note
    `eigvals!`が呼び出されると、入力行列`A`はその固有値を含まなくなります - `A`は作業スペースとして使用されます。


# 例

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
