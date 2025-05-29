```
insert_qudits!(register, loc::Int, nqudits::Int) -> register
insert_qudits!(loc::Int, nqudits::Int) -> λ(register)
```

Insert qudits to given register in state |0>. i.e. |psi> -> join(|psi>, |0...>, |psi>), increased bits have higher indices.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> insert_qudits!(reg, 2, 2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 7/7
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 7, Int64}}:
 0110001 ₍₂₎
 0110001 ₍₂₎
 0110001 ₍₂₎
```
