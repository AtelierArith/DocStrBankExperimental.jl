```
uniform_state([T=ComplexF64], n; nbatch=NoBatch(), no_transpose_storage=false)
```

Create a uniform state:

$$
\frac{1}{\sqrt{2^n}} \sum_{k=0}^{2^{n}-1} |k\rangle.
$$

This state can also be created by applying `H` (Hadmard gate) on $|00⋯00⟩$ state.

### Example

```jldoctest; setup=:(using Yao)
julia> uniform_state(4; nbatch=2)
BatchedArrayReg{2, ComplexF64, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 2

julia> uniform_state(ComplexF32, 4; nbatch=2)
BatchedArrayReg{2, ComplexF32, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 2
```
