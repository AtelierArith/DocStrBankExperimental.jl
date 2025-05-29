```
invorder!(register)
```

Inverse the locations of the register.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"010101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 6/6
    nlevel: 2

julia> measure(invorder!(reg); nshots=3)
3-element Vector{DitStr{2, 6, Int64}}:
 101010 ₍₂₎
 101010 ₍₂₎
 101010 ₍₂₎
```
