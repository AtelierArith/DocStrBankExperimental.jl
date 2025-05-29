```
insert_qubits!(register, loc::Int, nqubits::Int=1) -> register
insert_qubits!(loc::Int, nqubits::Int=1) -> λ(register)
```

Insert `n` qubits to given register in state |0>. It is an alias of [`insert_qudits!`](@ref) function.
