```
append_qubits!(register, n::Int) -> register
append_qubits!(n::Int) -> λ(register)
```

与えられたレジスタに状態 |0> の `n` 個のクディットを追加します。これは [`append_qudits!`](@ref) 関数のエイリアスです。
