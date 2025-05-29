```
put(pair) -> f(n)
```

Lazy curried version of [`put`](@ref).

### Examples

```jldoctest; setup=:(using Yao)
julia> put(1=>X)
(n -> put(n, 1 => X))
```
