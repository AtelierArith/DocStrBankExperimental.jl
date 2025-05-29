```
cache(x[, level=1; recursive=false])
```

Create a [`CachedBlock`](@ref) with given block `x`, which will cache the matrix of `x` for the first time it calls [`mat`](@ref), and use the cached matrix in the following calculations.

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> cache(control(3, 1, 2=>X))
nqubits: 3
[cached] control(1)
   └─ (2,) X


julia> chain(cache(control(3, 1, 2=>X)), repeat(H))
nqubits: 3
chain
└─ [cached] control(1)
      └─ (2,) X

```
