```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

Un itérateur qui accède à chaque élément du tableau `A`, retournant `i => x`, où `i` est l'indice de l'élément et `x = A[i]`. Identique à `pairs(A)`, sauf que le style de l'indice peut être sélectionné. Également similaire à `enumerate(A)`, sauf que `i` sera un indice valide pour `A`, tandis que `enumerate` compte toujours à partir de 1, indépendamment des indices de `A`.

Spécifier [`IndexLinear()`](@ref) garantit que `i` sera un entier ; spécifier [`IndexCartesian()`](@ref) garantit que `i` sera un [`Base.CartesianIndex`](@ref) ; spécifier `IndexStyle(A)` choisit celui qui a été défini comme le style d'indexation natif pour le tableau `A`.

La mutation des limites du tableau sous-jacent invalidera cet itérateur.

# Exemples

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

Voir aussi [`IndexStyle`](@ref), [`axes`](@ref).
