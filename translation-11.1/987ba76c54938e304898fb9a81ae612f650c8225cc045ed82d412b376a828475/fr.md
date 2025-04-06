```
errormonitor(t::Task)
```

Imprime un journal d'erreurs dans `stderr` si la tâche `t` échoue.

# Exemples

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("la tâche a échoué")))
Erreur de tâche non gérée : la tâche a échoué
Trace de la pile :
[...]
```
