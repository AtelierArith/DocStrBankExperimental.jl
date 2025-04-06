```
withenv(f, kv::Pair...)
```

Exécutez `f` dans un environnement qui est temporairement modifié (et non remplacé comme dans `setenv`) par zéro ou plusieurs arguments `"var"=>val` `kv`. `withenv` est généralement utilisé via la syntaxe `withenv(kv...) do ... end`. Une valeur de `nothing` peut être utilisée pour désactiver temporairement une variable d'environnement (si elle est définie). Lorsque `withenv` retourne, l'environnement d'origine a été restauré.

!!! warning
    Changer l'environnement n'est pas thread-safe. Pour exécuter des commandes externes avec un environnement différent de celui du processus parent, il est préférable d'utiliser [`addenv`](@ref) plutôt que `withenv`.

