```
measure([, operator], register[, locs]; nshots=1, rng=Random.GLOBAL_RNG) -> Vector{Int}
```

量子状態を測定し、quditの測定結果を返します。この測定関数は、入力状態を崩壊させない`measure!`の不正バージョンです。また、複数ショットの測定を行うために量子状態を再計算する必要もありません。

### 引数

  * `operator::AbstractBlock`は測定するオペレーターです。
  * `register::AbstractRegister`は量子状態です。
  * `locs`は測定を行うキュービットです。`locs`が提供されていない場合、すべての現在のアクティブなquditが測定されます（アクティブなquditについては、[`focus!`](@ref)および[`relax!`](@ref)を参照してください）。

### キーワード引数

  * `nshots::Int`はショットの数です。
  * `rng`は乱数生成器です。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"110")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 110 ₍₂₎
 110 ₍₂₎
 110 ₍₂₎

julia> measure(reg, (2,3); nshots=3)
3-element Vector{DitStr{2, 2, Int64}}:
 11 ₍₂₎
 11 ₍₂₎
 11 ₍₂₎
```

次の例では、測定のためにX基底に切り替えます。

```jldoctest; setup=:(using Yao)
julia> reg = apply!(product_state(bit"100"), repeat(3, H, 1:3))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(repeat(3, X, 1:3), reg; nshots=3)
3-element Vector{ComplexF64}:
 -1.0 + 0.0im
 -1.0 + 0.0im
 -1.0 + 0.0im

julia> reg = apply!(product_state(bit"101"), repeat(3, H, 1:3))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(repeat(3, X, 1:3), reg; nshots=3)
3-element Vector{ComplexF64}:
 1.0 - 0.0im
 1.0 - 0.0im
 1.0 - 0.0im
```
