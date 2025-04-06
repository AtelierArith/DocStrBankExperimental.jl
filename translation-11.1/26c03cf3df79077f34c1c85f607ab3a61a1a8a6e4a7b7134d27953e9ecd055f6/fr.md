```
prevfloat(x::AbstractFloat)
```

Retourne le plus grand nombre à virgule flottante `y` du même type que `x` tel que `y < x`. Si aucun `y` de ce type n'existe (par exemple, si `x` est `-Inf` ou `NaN`), alors retourne `x`.
