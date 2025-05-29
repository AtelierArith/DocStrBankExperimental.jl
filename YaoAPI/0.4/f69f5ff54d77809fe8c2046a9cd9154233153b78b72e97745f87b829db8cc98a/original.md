```
render_params(r::AbstractBlock, params)
```

This function renders the input parameter to a consumable type to `r`. `params` can be a number or a symbol like `:zero` and `:random`.

### Examples

```jldoctest; setup=:(using Yao)
julia> collect(render_params(Rx(0.1), :zero))
1-element Vector{Float64}:
 0.0
```
