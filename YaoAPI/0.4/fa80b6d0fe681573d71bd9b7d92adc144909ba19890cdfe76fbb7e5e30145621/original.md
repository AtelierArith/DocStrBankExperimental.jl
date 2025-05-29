```
niparam(block) -> Int
```

Return number of intrinsic parameters in `block`. See also [`nparameters`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> niparams(Rx(0.1))
1
```
