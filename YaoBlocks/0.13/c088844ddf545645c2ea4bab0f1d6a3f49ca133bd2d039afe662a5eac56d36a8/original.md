```
chain(n)
```

Return an empty [`ChainBlock`](@ref) which can be used like a list of blocks.

### Examples

```jldoctest; setup=:(using Yao)
julia> chain(2)
nqubits: 2
chain


julia> chain(2; nlevel=3)
nqudits: 2
chain


```
