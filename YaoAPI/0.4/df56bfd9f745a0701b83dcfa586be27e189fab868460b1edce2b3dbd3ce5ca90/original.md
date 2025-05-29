```
relax!(register[, locs]; to_nactive=nqudits(register)) -> register
relax!(locs::Int...; to_nactive=nqudits(register)) -> f(register) -> register
```

Inverse transformation of [`focus!`](@ref), where `to_nactive` is the number  of active bits for target register. If the register is not provided, returns a lambda function that takes a register as input.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> focus!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/5
    nlevel: 2

julia> relax!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2
```
