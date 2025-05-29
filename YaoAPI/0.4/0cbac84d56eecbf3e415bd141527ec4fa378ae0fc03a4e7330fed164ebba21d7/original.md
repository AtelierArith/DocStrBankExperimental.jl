```
parameters_eltype(x)
```

Return the element type of [`parameters`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> parameters_eltype(chain(Rx(0.1), Rz(0.1f0)))
Float64
```
