```
norm(x::Number, p::Real=2)
```

Pour les nombres, retourner $\left( |x|^p \right)^{1/p}$.

# Exemples

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
