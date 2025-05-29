```
arrayreg([T=ComplexF64], bit_str; nbatch=NoBatch())
```

Construct an array register from bit string literal. For bit string literal please read [`@bit_str`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> arrayreg(bit"1010")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> arrayreg(ComplexF32, bit"1010")
ArrayReg{2, ComplexF32, Array...}
    active qubits: 4/4
    nlevel: 2
```
