```
parameters(block)
```

Returns all the parameters contained in block tree with given root `block`.

### Examples

```jldoctest; setup=:(using Yao)
julia> parameters(chain(Rx(0.1), Rz(0.2)))
2-element Vector{Float64}:
 0.1
 0.2
```
