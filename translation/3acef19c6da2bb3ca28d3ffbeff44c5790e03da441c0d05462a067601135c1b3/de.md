```
norm(x::Number, p::Real=2)
```

Für Zahlen, geben Sie $\left( |x|^p \right)^{1/p}$ zurück.

# Beispiele

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
