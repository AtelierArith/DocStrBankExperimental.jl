```
atexit(f)
```

Enregistre une fonction `f()` à zéro ou un argument qui sera appelée à la sortie du processus. Les hooks `atexit()` sont appelés dans l'ordre dernier entré, premier sorti (LIFO) et s'exécutent avant les finaliseurs d'objet.

Si `f` a une méthode définie pour un argument entier, elle sera appelée comme `f(n::Int32)`, où `n` est le code de sortie actuel, sinon elle sera appelée comme `f()`.

!!! compat "Julia 1.9"
    La forme à un argument nécessite Julia 1.9


Les hooks de sortie sont autorisés à appeler `exit(n)`, auquel cas Julia sortira avec le code de sortie `n` (au lieu du code de sortie original). Si plus d'un hook de sortie appelle `exit(n)`, alors Julia sortira avec le code de sortie correspondant au dernier hook de sortie appelé qui appelle `exit(n)`. (Parce que les hooks de sortie sont appelés dans l'ordre LIFO, "dernier appelé" est équivalent à "premier enregistré".)

Remarque : Une fois que tous les hooks de sortie ont été appelés, aucun autre hook de sortie ne peut être enregistré, et tout appel à `atexit(f)` après que tous les hooks ont été complétés lancera une exception. Cette situation peut se produire si vous enregistrez des hooks de sortie à partir de Tâches en arrière-plan qui peuvent encore s'exécuter de manière concurrente pendant l'arrêt.
