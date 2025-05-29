```
swap(loc1, loc2) -> f(n)
```

Create a lambda that takes the total number of active qubits as input. Lazy curried version of `swap(n, loc1, loc2)`. See also [`Swap`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> swap(1, 2)
(n -> swap(n, 1, 2))
```
