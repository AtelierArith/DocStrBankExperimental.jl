```
AbstractRegister{D}
```

Abstract type for quantum registers. Type parameter `D` is the number of levels in each qudit. For qubits, `D = 2`.

### Required methods

  * [`instruct!`](@ref)
  * [`nqudits`](@ref)
  * [`nactive`](@ref)
  * [`insert_qubits!`](@ref)
  * [`append_qubits!`](@ref)
  * [`focus!`](@ref)
  * [`relax!`](@ref)
  * [`reorder!`](@ref)
  * [`invorder!`](@ref)

### Optional methods

  * [`nlevel`](@ref)
  * [`nremain`](@ref)
