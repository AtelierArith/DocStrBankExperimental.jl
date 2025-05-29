```
zero_state([T=ComplexF64], n::Int; nbatch::Int=NoBatch())
```

Create an [`AbstractArrayReg`](@ref) that initialized to state $|0\rangle^{\otimes n}$. See also [`product_state`](@ref), [`rand_state`](@ref), [`uniform_state`](@ref) and [`ghz_state`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> zero_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> zero_state(ComplexF32, 4)
ArrayReg{2, ComplexF32, Array...}
    active qubits: 4/4
    nlevel: 2

julia> zero_state(ComplexF32, 4; nbatch=3)
BatchedArrayReg{2, ComplexF32, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 3
```
