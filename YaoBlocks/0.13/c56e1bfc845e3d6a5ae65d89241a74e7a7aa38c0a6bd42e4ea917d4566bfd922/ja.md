```
unitary_channel(operators, probs) -> UnitaryChannel
```

[`UnitaryChannel`](@ref) インスタンスを返します。ここで ``operators` はオペレーターのリストで、`probs` は合計が1になる実数ベクトルです。ユニタリチャネルは以下のように定義されます。

$$
\phi(\rho) = \sum_i p_i U_i ρ U_i^\dagger,
$$

ここで $\rho$ は [`DensityMatrix`](@ref) であり、適用するレジスタです。$p_i$ は `probs` の i 番目の要素、`U_i` は `operators` の i 番目のオペレーターです。

### 例

```jldoctest; setup=:(using Yao)
julia> unitary_channel([X, Y, Z], [0.1, 0.2, 0.7])
nqubits: 1
unitary_channel
├─ [0.1] X
├─ [0.2] Y
└─ [0.7] Z
```
