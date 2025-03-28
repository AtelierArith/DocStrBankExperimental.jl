```
@inbounds(blk)
```

Élimine la vérification des limites de tableau dans les expressions.

Dans l'exemple ci-dessous, la vérification de la plage pour référencer l'élément `i` du tableau `A` est ignorée pour améliorer les performances.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! avertissement
    L'utilisation de `@inbounds` peut renvoyer des résultats incorrects/faire planter/corrompre pour des indices hors limites. L'utilisateur est responsable de la vérification manuelle. N'utilisez `@inbounds` que lorsqu'il est certain, d'après les informations disponibles localement, que tous les accès sont dans les limites. En particulier, utiliser `1:length(A)` au lieu de `eachindex(A)` dans une fonction comme celle ci-dessus n'est *pas* en toute sécurité dans les limites, car le premier indice de `A` peut ne pas être `1` pour tous les types définis par l'utilisateur qui sous-type `AbstractArray`.

