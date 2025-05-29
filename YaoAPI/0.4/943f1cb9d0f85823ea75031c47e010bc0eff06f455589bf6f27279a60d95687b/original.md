```
content(x) -> block
```

Returns the content of `x`, this is a specific API for [`AbstractContainer`](@ref) that returns a block.

### Examples

```jldoctest; setup=:(using Yao)
julia> content(2.0 * X)
X
```
