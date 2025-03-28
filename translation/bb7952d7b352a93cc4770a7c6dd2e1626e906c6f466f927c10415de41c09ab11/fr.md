```
\(A, B)
```

Division de matrices utilisant un polyalgorithme. Pour les matrices d'entrée `A` et `B`, le résultat `X` est tel que `A*X == B` lorsque `A` est carrée. Le solveur utilisé dépend de la structure de `A`. Si `A` est triangulaire supérieure ou inférieure (ou diagonale), aucune factorisation de `A` n'est requise et le système est résolu par substitution avant ou arrière. Pour les matrices carrées non triangulaires, une factorisation LU est utilisée.

Pour `A` rectangulaire, le résultat est la solution des moindres carrés à norme minimale calculée par une factorisation QR pivotée de `A` et une estimation du rang de `A` basée sur le facteur R.

Lorsque `A` est sparse, un polyalgorithme similaire est utilisé. Pour les matrices indéfinies, la factorisation `LDLt` n'utilise pas de pivotement pendant la factorisation numérique et par conséquent, la procédure peut échouer même pour des matrices inversibles.

Voir aussi : [`factorize`](@ref), [`pinv`](@ref).

# Exemples

```jldoctest
julia> A = [1 0; 1 -2]; B = [32; -4];

julia> X = A \ B
2-element Vector{Float64}:
 32.0
 18.0

julia> A * X == B
true
```
