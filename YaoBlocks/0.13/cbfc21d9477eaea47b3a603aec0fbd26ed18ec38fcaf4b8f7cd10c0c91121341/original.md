```
cnot([n, ]ctrl_locs, location)
```

Return a speical [`ControlBlock`](@ref), aka CNOT gate with number of active qubits `n` and locs of control qubits `ctrl_locs`, and `location` of `X` gate.

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> cnot(3, (2, 3), 1)
nqubits: 3
control(2, 3)
└─ (1,) X

julia> cnot(2, 1)
(n -> cnot(n, 2, 1))
```
