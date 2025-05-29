```
withjacobian(f, args...)
```

Returns both the value `f(args...)` and the [`jacobian`](@ref) as a named tuple.

```jldoctest; setup=:(using Zygote)
julia> withjacobian(cumsum, [1,2,3])
(val = [1, 3, 6], grad = ([1 0 0; 1 1 0; 1 1 1],))
```
