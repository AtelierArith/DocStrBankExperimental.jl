```
mod(x::Integer, r::AbstractUnitRange)
```

Trouvez `y` dans l'intervalle `r` tel que $x ≡ y (mod n)$, où `n = length(r)`, c'est-à-dire `y = mod(x - first(r), n) + first(r)`.

Voir aussi [`mod1`](@ref).

# Exemples

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! compat "Julia 1.3"
    Cette méthode nécessite au moins Julia 1.3.

