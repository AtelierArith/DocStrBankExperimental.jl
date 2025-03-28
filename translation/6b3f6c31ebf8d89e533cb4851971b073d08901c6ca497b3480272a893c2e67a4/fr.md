```
mapreduce(f, op, itrs...; [init])
```

Applique la fonction `f` à chaque élément(s) dans `itrs`, puis réduit le résultat en utilisant la fonction binaire `op`. Si fourni, `init` doit être un élément neutre pour `op` qui sera retourné pour les collections vides. Il n'est pas spécifié si `init` est utilisé pour les collections non vides. En général, il sera nécessaire de fournir `init` pour travailler avec des collections vides.

[`mapreduce`](@ref) est fonctionnellement équivalent à appeler `reduce(op, map(f, itr); init=init)`, mais s'exécutera généralement plus rapidement car aucune collection intermédiaire n'a besoin d'être créée. Voir la documentation pour [`reduce`](@ref) et [`map`](@ref).

!!! compat "Julia 1.2"
    `mapreduce` avec plusieurs itérateurs nécessite Julia 1.2 ou une version ultérieure.


# Exemples

```jldoctest
julia> mapreduce(x->x^2, +, [1:3;]) # == 1 + 4 + 9
14
```

L'associativité de la réduction dépend de l'implémentation. De plus, certaines implémentations peuvent réutiliser la valeur de retour de `f` pour les éléments qui apparaissent plusieurs fois dans `itr`. Utilisez [`mapfoldl`](@ref) ou [`mapfoldr`](@ref) à la place pour garantir l'associativité gauche ou droite et l'invocation de `f` pour chaque valeur.
