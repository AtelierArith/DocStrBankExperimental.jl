```
AbstractRegister{D}
```

量子レジスタのための抽象型。型パラメータ `D` は各クディットのレベル数です。キュービットの場合、`D = 2` です。

### 必要なメソッド

  * [`instruct!`](@ref)
  * [`nqudits`](@ref)
  * [`nactive`](@ref)
  * [`insert_qubits!`](@ref)
  * [`append_qubits!`](@ref)
  * [`focus!`](@ref)
  * [`relax!`](@ref)
  * [`reorder!`](@ref)
  * [`invorder!`](@ref)

### オプションのメソッド

  * [`nlevel`](@ref)
  * [`nremain`](@ref)
