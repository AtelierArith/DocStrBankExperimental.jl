```
cumprod!(y::AbstractVector, x::AbstractVector)
```

Produit cumulatif d'un vecteur `x`, stockant le résultat dans `y`. Voir aussi [`cumprod`](@ref).

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

