```
insert_qudits!(register, loc::Int; nqudits::Int=1) -> register
insert_qudits!(loc::Int; nqudits::Int=1) -> λ(register)
```

与えられたレジスタに状態 |0> の `n` 個のクディットを挿入します。すなわち、|psi> -> |psi> ⊗ |000> ⊗ |psi> であり、増加したビットはより高いインデックスを持ちます。

整数のみが提供された場合、ラムダ関数を返します。
