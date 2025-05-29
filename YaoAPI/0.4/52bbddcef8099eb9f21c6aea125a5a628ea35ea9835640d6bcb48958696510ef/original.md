```
clone(register, n)
```

Create an [`ArrayReg`](@ref) by cloning the original `register` for `n` times on batch dimension. This function is only for emulation.

# Example

```jldoctest; setup=:(using YaoArrayRegister)
julia> clone(arrayreg(bit"101"; nbatch=3), 4)
BatchedArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2
    nbatch: 12
```
