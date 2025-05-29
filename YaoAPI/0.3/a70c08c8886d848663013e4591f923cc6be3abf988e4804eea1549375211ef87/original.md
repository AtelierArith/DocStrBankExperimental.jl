```
insert_qubits!(register, loc::Int; nqubits::Int=1) -> register
insert_qubits!(loc::Int; nqubits::Int=1) -> λ(register)
```

Insert `n` qubits to given register in state |0>. i.e. |psi> -> |psi> ⊗ |000> ⊗ |psi>, increased bits have higher indices.

If only an integer is provided, then returns a lambda function.
