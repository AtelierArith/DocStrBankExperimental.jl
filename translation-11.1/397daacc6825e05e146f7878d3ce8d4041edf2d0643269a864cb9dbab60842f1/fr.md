```
CachingPool(workers::Vector{Int})
```

Une implémentation d'un `AbstractWorkerPool`. [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref) (et d'autres appels distants qui exécutent des fonctions à distance) bénéficient de la mise en cache des fonctions sérialisées/désérialisées sur les nœuds de travail, en particulier les fermetures (qui peuvent capturer de grandes quantités de données).

Le cache distant est maintenu pendant la durée de vie de l'objet `CachingPool` retourné. Pour vider le cache plus tôt, utilisez `clear!(pool)`.

Pour les variables globales, seules les liaisons sont capturées dans une fermeture, pas les données. Des blocs `let` peuvent être utilisés pour capturer des données globales.

# Exemples

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

Ce qui précède transférerait `foo` une seule fois à chaque travailleur.
