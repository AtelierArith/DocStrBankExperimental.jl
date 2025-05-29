```
control(ctrl_locs, target) -> f(n)
```

Return a lambda that takes the number of total active qubits as input. See also [`control`](@ref).

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> control((2, 3), 1=>X)
(n -> control(n, (2, 3), 1 => X))

julia> control(2, 1=>X)
(n -> control(n, 2, 1 => X))
```
