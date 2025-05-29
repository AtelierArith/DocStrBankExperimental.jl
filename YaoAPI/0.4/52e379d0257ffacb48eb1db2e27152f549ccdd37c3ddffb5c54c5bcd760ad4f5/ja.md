```
insert_qubits!(register, loc::Int, nqubits::Int=1) -> register
insert_qubits!(loc::Int, nqubits::Int=1) -> λ(register)
```

指定されたレジスタに状態 |0> の `n` 個のキュービットを挿入します。これは [`insert_qudits!`](@ref) 関数のエイリアスです。
