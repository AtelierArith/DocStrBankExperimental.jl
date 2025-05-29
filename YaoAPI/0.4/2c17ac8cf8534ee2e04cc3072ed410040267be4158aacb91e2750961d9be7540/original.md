```
nparameters(block) -> Int
```

Return number of parameters in `block`. See also [`niparams`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> nparameters(chain(Rx(0.1), Rz(0.2)))
2
```
