```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

Exécutez les tests unitaires Julia listés dans `tests`, qui peuvent être soit une chaîne de caractères, soit un tableau de chaînes de caractères, en utilisant `ncores` processeurs. Si `exit_on_error` est `false`, lorsqu'un test échoue, tous les tests restants dans d'autres fichiers seront tout de même exécutés ; sinon, ils sont abandonnés lorsque `exit_on_error == true`. Si `revise` est `true`, le package `Revise` est utilisé pour charger toute modification apportée à `Base` ou aux bibliothèques standard avant d'exécuter les tests. Si une graine est fournie via l'argument clé, elle est utilisée pour initialiser le RNG global dans le contexte où les tests sont exécutés ; sinon, la graine est choisie aléatoirement.
