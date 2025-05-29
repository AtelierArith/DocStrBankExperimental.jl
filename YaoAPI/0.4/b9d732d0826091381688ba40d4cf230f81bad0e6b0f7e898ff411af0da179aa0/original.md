```
density_matrix(register_or_rho[, locations])
```

Returns the reduced density matrix for qubits at `locations` (default: all qubits).

### Examples

The following code gets the single site reduce density matrix for the GHZ state.

```jldoctest; setup=:(using Yao)
julia> reg = ghz_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> density_matrix(reg, (2,)).state
2×2 Matrix{ComplexF64}:
 0.5+0.0im  0.0+0.0im
 0.0-0.0im  0.5+0.0im
```
