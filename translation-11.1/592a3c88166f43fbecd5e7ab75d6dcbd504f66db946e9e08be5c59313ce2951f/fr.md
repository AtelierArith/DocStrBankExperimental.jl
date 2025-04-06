```
@big_str str
```

Analyse une chaîne de caractères en un [`BigInt`](@ref) ou un [`BigFloat`](@ref), et lance une `ArgumentError` si la chaîne n'est pas un nombre valide. Pour les entiers, `_` est autorisé dans la chaîne comme séparateur.

# Exemples

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: format de nombre invalide _ pour BigInt ou BigFloat
[...]
```

!!! avertissement
    Utiliser `@big_str` pour construire des valeurs [`BigFloat`](@ref) peut ne pas donner le comportement qui pourrait être naïvement attendu : en tant que macro, `@big_str` obéit à la précision globale ([`setprecision`](@ref)) et aux paramètres de mode d'arrondi ([`setrounding`](@ref)) tels qu'ils sont au *moment du chargement*. Ainsi, une fonction comme `() -> precision(big"0.3")` renvoie une constante dont la valeur dépend de la valeur de la précision au moment où la fonction est définie, **et non** de la précision au moment où la fonction est appelée.

