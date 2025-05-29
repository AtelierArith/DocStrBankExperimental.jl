```
von_neumann_entropy(reg::AbstractArrayReg, part)
von_neumann_entropy(ρ::DensityMatrix)
```

The entanglement entropy between `part` and the rest part in quantum state `reg`. If the input is a density matrix, it returns the entropy of a mixed state.

### Example

The Von Neumann entropy of any segment of GHZ state is $\log 2$.

```jldoctest; setup=:(using Yao)
julia> von_neumann_entropy(ghz_state(3), (1,2))
0.6931471805599612
```
