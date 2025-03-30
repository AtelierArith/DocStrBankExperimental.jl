```
norm(x::Number, p::Real=2)
```

Sayılar için, $\left( |x|^p \right)^{1/p}$ değerini döndür.

# Örnekler

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
