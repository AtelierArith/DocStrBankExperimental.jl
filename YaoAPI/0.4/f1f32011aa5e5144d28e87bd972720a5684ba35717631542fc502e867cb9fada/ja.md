```
expect(op::AbstractBlock, reg) -> Vector
expect(op::AbstractBlock, reg => circuit) -> Vector
expect(op::AbstractBlock, density_matrix) -> Vector
```

演算子の期待値を取得します。第二引数はレジスタ `reg` または入力レジスタと回路のペア `reg => circuit` であることができます。

```
expect'(op::AbstractBlock, reg=>circuit) -> Pair
expect'(op::AbstractBlock, reg) -> AbstracRegister
```

レジスタと回路パラメータに関する勾配を取得します。ペア入力の場合、第二の戻り値は `gψ=>gparams` のペアであり、`gψ` は入力状態の勾配、`gparams` は回路パラメータの勾配です。レジスタ入力の場合、戻り値はレジスタです。

!!! note
    バッチレジスタの場合、`expect(op, reg=>circuit)` は出力としてバッチ数のサイズのベクトルを返します。しかし、ベクトル損失に対して微分を行うことはできないため、`expect'(op, reg=>circuit)` はバッチ全体の勾配を蓄積し、パラメータのバッチ勾配を返すのではありません。


### 例

```jldoctest; setup=:(using Yao)
julia> r = normalize!(product_state(bit"11") + product_state(bit"00"))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> op = chain(2, put(1=>H), put(2=>X))
nqubits: 2
chain
├─ put on (1)
│  └─ H
└─ put on (2)
   └─ X


julia> expect(op, r)
0.7071067811865474
```
