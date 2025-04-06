```
remote_do(f, id::Integer, args...; kwargs...) -> nothing
```

Exécute `f` sur le travailleur `id` de manière asynchrone. Contrairement à [`remotecall`](@ref), il ne stocke pas le résultat du calcul, ni il n'y a de moyen d'attendre son achèvement.

Une invocation réussie indique que la demande a été acceptée pour exécution sur le nœud distant.

Alors que les appels consécutifs à `remotecall` vers le même travailleur sont sérialisés dans l'ordre où ils sont invoqués, l'ordre des exécutions sur le travailleur distant est indéterminé. Par exemple, `remote_do(f1, 2); remotecall(f2, 2); remote_do(f3, 2)` va sérialiser l'appel à `f1`, suivi de `f2` et `f3` dans cet ordre. Cependant, il n'est pas garanti que `f1` soit exécuté avant `f3` sur le travailleur 2.

Toutes les exceptions levées par `f` sont imprimées sur [`stderr`](@ref) sur le travailleur distant.

Les arguments de mot-clé, le cas échéant, sont transmis à `f`.
