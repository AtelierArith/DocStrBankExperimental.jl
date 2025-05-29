```
subblocks(x)
```

Returns an iterator of the sub-blocks of a composite block. Default is empty.

### Examples

```jldoctest; setup=:(using Yao)
julia> subblocks(chain(X, Y, Z))
3-element Vector{AbstractBlock{2}}:
 X
 Y
 Z
```
