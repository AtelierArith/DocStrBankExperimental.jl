```
islocked(lock) -> Statut (Booléen)
```

Vérifiez si le `lock` est détenu par une tâche/fil. Cette fonction seule ne doit pas être utilisée pour la synchronisation. Cependant, `islocked` combiné avec [`trylock`](@ref) peut être utilisé pour écrire les algorithmes de test-et-test-et-set ou de retour exponentiel *si cela est supporté par le `typeof(lock)`* (lisez sa documentation).

# Aide étendue

Par exemple, un retour exponentiel peut être implémenté comme suit si l'implémentation du `lock` satisfait les propriétés documentées ci-dessous.

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("timeout")
    end
    trylock(lock) && break
    backoff()
end
```

## Implémentation

Il est conseillé à une implémentation de lock de définir `islocked` avec les propriétés suivantes et de le noter dans sa docstring.

  * `islocked(lock)` est sans course de données.
  * Si `islocked(lock)` retourne `false`, une invocation immédiate de `trylock(lock)` doit réussir (retourne `true`) s'il n'y a pas d'interférence d'autres tâches.
