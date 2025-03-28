```
norm(x::Number, p::Real=2)
```

Para números, devuelve $\left( |x|^p \right)^{1/p}$.

# Ejemplos

```jldoctest
julia> norm(2, 1)
2.0

julia> norm(-2, 1)
2.0

julia> norm(2, 2)
2.0

julia> norm(-2, 2)
2.0

julia> norm(2, Inf)
2.0

julia> norm(-2, Inf)
2.0
```
