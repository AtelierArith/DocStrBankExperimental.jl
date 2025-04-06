```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

Obtenez la précision d'un nombre à virgule flottante, telle que définie par le nombre effectif de bits dans le significand, ou la précision d'un type à virgule flottante `T` (sa valeur par défaut actuelle, si `T` est un type à précision variable comme [`BigFloat`](@ref)).

Si `base` est spécifié, alors il renvoie le nombre maximum correspondant de chiffres de significand dans cette base.

!!! compat "Julia 1.8"
    Le mot-clé `base` nécessite au moins Julia 1.8.

