```
typeof(x)
```

Obtenez le type concret de `x`.

Voir aussi [`eltype`](@ref).

# Exemples

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias pour Array{Float64, 2})
```
