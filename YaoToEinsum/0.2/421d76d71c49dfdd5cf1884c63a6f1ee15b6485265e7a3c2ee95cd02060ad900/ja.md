```
optimize_code(c::TensorNetwork, optimizer=TreeSA())
```

テンソルネットワークのコードを最適化します。

### 引数

  * `c::TensorNetwork`: テンソルネットワーク。
  * `optimizer::Optimizer`: 使用する最適化手法、デフォルトは `TreeSA()` です。詳細については [OMEinsumContractors.jl](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) をご覧ください。
