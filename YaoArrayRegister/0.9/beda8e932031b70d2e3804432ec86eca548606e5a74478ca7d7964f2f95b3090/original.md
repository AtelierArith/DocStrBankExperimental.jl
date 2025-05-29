```
zero_state_like(register, n) -> AbstractRegister
```

Create a register initialized to zero from an existing one.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = rand_state(3; nbatch=2);

julia> zero_state_like(reg, 2)
BatchedArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2
    nbatch: 2
```
