```
insert_qudits!(register, loc::Int; nqudits::Int=1) -> register
insert_qudits!(loc::Int; nqudits::Int=1) -> λ(register)
```

Insert `n` qudits to given register in state |0>. i.e. |psi> -> |psi> ⊗ |000> ⊗ |psi>, increased bits have higher indices.

If only an integer is provided, then returns a lambda function.
