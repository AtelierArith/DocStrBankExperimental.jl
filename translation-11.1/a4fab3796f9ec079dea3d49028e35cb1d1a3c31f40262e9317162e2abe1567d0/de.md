```
typeof(x)
```

Erhalte den konkreten Typ von `x`.

Siehe auch [`eltype`](@ref).

# Beispiele

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias für Array{Float64, 2})
```
