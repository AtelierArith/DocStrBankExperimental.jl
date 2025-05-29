```
rand_state([T=ComplexF64], n::Int; nbatch=NoBatch(), no_transpose_storage=false)
```

Create a random [`AbstractArrayReg`](@ref) with total number of qudits `n`.

### Examples

```jldoctest; setup=:(using Yao)
julia> rand_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> rand_state(ComplexF64, 4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> rand_state(ComplexF64, 4; nbatch=2)
BatchedArrayReg{2, ComplexF64, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 2
```
