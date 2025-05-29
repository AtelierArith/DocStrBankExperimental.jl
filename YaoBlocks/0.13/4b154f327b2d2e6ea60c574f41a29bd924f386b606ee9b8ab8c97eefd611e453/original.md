```
swap(n, loc1, loc2)
```

Create a `n`-qubit [`Swap`](@ref) gate which swap `loc1` and `loc2`.

### Examples

```jldoctest; setup=:(using Yao)
julia> swap(4, 1, 2)
nqubits: 4
put on (1, 2)
└─ SWAP
```
