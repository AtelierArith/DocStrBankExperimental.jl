```
Measure(n::Int; rng=Random.GLOBAL_RNG, operator=ComputationalBasis(), locs=AllLocs(), resetto=nothing, remove=false)
```

数のqudit `n`を持つ`Measure`ブロックを作成します。

### 例

与えられた基底上に`Measure`ブロックを作成できます（デフォルトは計算基底です）。

```jldoctest; setup=:(using Yao)
julia> Measure(4)
Measure(4)
```

また、測定するquditを指定することもできます。

```jldoctest; setup=:(using Yao)
julia> Measure(4; locs=1:3)
Measure(4;locs=(1, 2, 3))
```

デフォルトでは、これは現在のレジスタを測定結果に崩壊させます。

```jldoctest; setup=:(using Yao, Random; Random.seed!(123))
julia> r = normalize!(arrayreg(bit"000") + arrayreg(bit"111"))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> state(r)
8×1 Matrix{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> r |> Measure(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> state(r)
8×1 Matrix{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 1.0 + 0.0im
```

ただし、`resetto`キーワードを使用して、崩壊させたいターゲットビット構成を指定することもできます。

```jldoctest; setup=:(using Yao) julia> m = Measure(4; resetto=bit"0101") Measure(4;postprocess=ResetTo{BitStr{4,Int64}}(0101 ₍₂₎))

julia> m.postprocess ResetTo{BitStr{4,Int64}}(0101 ₍₂₎)```
