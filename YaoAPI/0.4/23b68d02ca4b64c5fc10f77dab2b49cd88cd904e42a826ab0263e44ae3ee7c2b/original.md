```
iparams_eltype(block)
```

Return the element type of [`getiparams`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> iparams_eltype(Rx(0.1))
Float64
```
