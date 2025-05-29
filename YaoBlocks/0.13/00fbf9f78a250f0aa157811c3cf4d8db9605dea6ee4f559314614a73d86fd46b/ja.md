```
expect(op::AbstractBlock, reg) -> Real
expect(op::AbstractBlock, reg => circuit) -> Real
expect(op::AbstractBlock, density_matrix) -> Real
```

演算子の期待値を取得します。第二引数はレジスタ `reg` または入力レジスタと回路のペア `reg => circuit` です。

expect'(op::AbstractBlock, reg=>circuit) -> Pair expect'(op::AbstractBlock, reg) -> AbstracRegister

レジスタと回路パラメータに関する勾配を取得します。ペア入力の場合、第二の戻り値は `gψ=>gparams` のペアで、`gψ` は入力状態の勾配、`gparams` は回路パラメータの勾配です。レジスタ入力の場合、戻り値はレジスタです。

!!! note
    バッチレジスタの場合、`expect(op, reg=>circuit)` は出力としてバッチ数のサイズのベクトルを返します。しかし、ベクトル損失に対して微分を行うことはできないため、`expect'(op, reg=>circuit)` はバッチ全体の勾配を蓄積し、パラメータのバッチ勾配を返すのではありません。

