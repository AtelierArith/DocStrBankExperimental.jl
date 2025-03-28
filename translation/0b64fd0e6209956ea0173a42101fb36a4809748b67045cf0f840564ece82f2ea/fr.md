```
nextfloat(x::AbstractFloat)
```

Retourne le plus petit nombre à virgule flottante `y` du même type que `x` tel que `x < y`. Si aucun `y` de ce type n'existe (par exemple si `x` est `Inf` ou `NaN`), alors retourne `x`.

Voir aussi : [`prevfloat`](@ref), [`eps`](@ref), [`issubnormal`](@ref).
