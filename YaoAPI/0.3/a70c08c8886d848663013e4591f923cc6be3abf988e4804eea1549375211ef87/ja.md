```
insert_qubits!(register, loc::Int; nqubits::Int=1) -> register
insert_qubits!(loc::Int; nqubits::Int=1) -> λ(register)
```

指定されたレジスタに状態 |0> の `n` 個のキュービットを挿入します。すなわち、|psi> -> |psi> ⊗ |000> ⊗ |psi> であり、追加されたビットは高いインデックスを持ちます。

整数のみが提供された場合、ラムダ関数を返します。
