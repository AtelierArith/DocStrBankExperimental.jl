```
cz([n, ]ctrl_locs, location)
```

Return a special [`ControlBlock`](@ref), aka CZ gate with number of active qubits `n` and locs of control qubits `ctrl_locs`, and `location` of `Z` gate. See also [`cnot`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> cz(2, 1, 2)
nqubits: 2
control(1)
└─ (2,) Z
```
