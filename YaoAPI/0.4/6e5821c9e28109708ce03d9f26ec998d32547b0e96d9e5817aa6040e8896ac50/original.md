```
apply!(register, block)
```

Apply a block (of quantum circuit) to a quantum register.

!!! note
    to overload `apply!` for a new block, please overload the [`unsafe_apply!`](@ref) function with same interface. Then the `apply!` interface will do the size checks on inputs automatically.


### Examples

```jldoctest; setup=:(using Yao)
julia> r = zero_state(2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> apply!(r, put(2, 1=>X))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> measure(r;nshots=10)
10-element Vector{DitStr{2, 2, Int64}}:
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
```
