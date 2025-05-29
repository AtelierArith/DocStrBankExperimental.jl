```
append_qudits!(register, n::Int) -> register
append_qudits!(n::Int) -> λ(register)
```

Add `n` qudits to given register in state |0>. i.e. |psi> -> |000> ⊗ |psi>, increased bits have higher indices.

If only an integer is provided, then returns a lambda function.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> append_qudits!(reg, 2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 7/7
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 7, Int64}}:
 0001101 ₍₂₎
 0001101 ₍₂₎
 0001101 ₍₂₎
```

Note here, we read the bit string from right to left.
