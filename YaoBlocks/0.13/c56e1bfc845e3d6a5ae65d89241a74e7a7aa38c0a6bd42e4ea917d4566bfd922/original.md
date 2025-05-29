```
unitary_channel(operators, probs) -> UnitaryChannel
```

Returns a [`UnitaryChannel`](@ref) instance, where ``operators` is a list of operators, `probs` is a real vector that sum up to 1. The unitary channel is defined as below

$$
\phi(\rho) = \sum_i p_i U_i ρ U_i^\dagger,
$$

where $\rho$ in a [`DensityMatrix`](@ref) as the register to apply on, $p_i$ is the i-th element in `probs`, `U_i` is the i-th operator in `operators`.

### Examples

```jldoctest; setup=:(using Yao)
julia> unitary_channel([X, Y, Z], [0.1, 0.2, 0.7])
nqubits: 1
unitary_channel
├─ [0.1] X
├─ [0.2] Y
└─ [0.7] Z
```
