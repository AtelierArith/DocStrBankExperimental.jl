```
probs(register) -> Vector
```

Returns the probability distribution of computation basis, aka $|<x|ψ>|^2$.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"101");

julia> reg |> probs
8-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 1.0
 0.0
 0.0
```
