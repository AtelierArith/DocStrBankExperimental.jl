```
pswap(n::Int, i::Int, j::Int, α::Real)
pswap(i::Int, j::Int, α::Real) -> f(n)

パラメータ化されたスワップゲート。

### 例

```

jldoctest; setup=:(using Yao) julia> pswap(2, 1, 2, 0.1) nqubits: 2 put on (1, 2) └─ rot(SWAP, 0.1) ```
