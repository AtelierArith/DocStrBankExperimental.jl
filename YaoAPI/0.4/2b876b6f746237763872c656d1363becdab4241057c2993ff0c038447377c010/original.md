```
chsubblocks(composite_block, itr)
```

Change the sub-blocks of a [`CompositeBlock`](@ref) with given iterator `itr`.

### Examples

```jldoctest; setup=:(using Yao)
julia> chsubblocks(chain(X, Y, Z), [Z, Z])
nqubits: 1
chain
├─ Z
└─ Z
```
