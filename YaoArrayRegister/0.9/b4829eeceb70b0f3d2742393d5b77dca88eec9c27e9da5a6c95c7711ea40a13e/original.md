```
ghz_state([T=ComplexF64], n::Int; nbatch::Int=NoBatch())
```

Create a GHZ state (or a cat state) that defined as

$$
\frac{|0\rangle^{\otimes n} + |1\rangle^{\otimes n}}{\sqrt{2}}.
$$

### Examples

```jldoctest; setup=:(using Yao)
julia> ghz_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2
```
