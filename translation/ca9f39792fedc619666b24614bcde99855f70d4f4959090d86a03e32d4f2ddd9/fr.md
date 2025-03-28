```
divrem(x, y, r::RoundingMode=RoundToZero)
```

Le quotient et le reste de la division euclidienne. Équivalent à `(div(x, y, r), rem(x, y, r))`. Équivalemment, avec la valeur par défaut de `r`, cet appel est équivalent à `(x ÷ y, x % y)`.

Voir aussi : [`fldmod`](@ref), [`cld`](@ref).

# Exemples

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
