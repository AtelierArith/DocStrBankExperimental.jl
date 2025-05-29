```
apply_back!((ψ, ∂L/∂ψ*), circuit::AbstractBlock, collector) -> AbstractRegister
```

逆伝播を行い、勾配 ∂L/∂θ = 2*Re(∂L/∂ψ*⋅∂ψ*/∂θ) を計算します。ここで、∂L/∂ψ* が与えられます。`ψ` は出力レジスタであり、∂L/∂ψ* もレジスタ型である必要があります。

注意: 勾配は `Diff` ブロックに保存され、`diffblock.grad` または `gradient(circuit)` のいずれかでアクセスできます。注意2: 現在、`apply_back!` は逆勾配を返します！
