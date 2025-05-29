```
exchange_sysenv(reg::AbstractArrayReg) -> AbstractRegister
```

Exchange system (focused qubits) and environment (remaining qubits).

```jldoctest; setup=:(using Yao)
julia> reg = rand_state(5)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> focus!(reg, (2,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/5
    nlevel: 2

julia> exchange_sysenv(reg)
ArrayReg{2, ComplexF64, Adjoint...}
    active qubits: 3/5
    nlevel: 2
```
