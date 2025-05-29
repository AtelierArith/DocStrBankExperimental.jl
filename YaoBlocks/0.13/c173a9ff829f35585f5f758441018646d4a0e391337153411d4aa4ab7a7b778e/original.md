```
kron(blocks::AbstractBlock...)
kron(n, itr)
```

Return a [`KronBlock`](@ref), with total number of qubits `n`, and `blocks` should use all the locations on `n` wires in quantum circuits.

### Examples

You can use kronecker product to composite small blocks to a large blocks.

```jldoctest; setup=:(using Yao)
julia> kron(X, Y, Z, Z)
nqubits: 4
kron
├─ 1=>X
├─ 2=>Y
├─ 3=>Z
└─ 4=>Z
```
