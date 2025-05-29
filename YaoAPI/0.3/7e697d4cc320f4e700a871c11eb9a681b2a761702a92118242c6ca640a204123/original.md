```
adddits!(register, n::Int) -> register
adddits!(n::Int) -> λ(register)
```

Add `n` qudits to given register in state |0>. i.e. |psi> -> |000> ⊗ |psi>, increased bits have higher indices.

If only an integer is provided, then returns a lambda function.
