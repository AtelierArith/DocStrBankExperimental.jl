```
trylock(lock) -> Succès (Booléen)
```

Acquérir le verrou s'il est disponible et retourner `true` si réussi. Si le verrou est déjà verrouillé par une autre tâche/fil, retourner `false`.

Chaque `trylock` réussi doit être associé à un [`unlock`](@ref).

La fonction `trylock` combinée avec [`islocked`](@ref) peut être utilisée pour écrire les algorithmes de test-et-test-et-set ou de retour exponentiel *si cela est supporté par le `typeof(lock)`* (lisez sa documentation).
