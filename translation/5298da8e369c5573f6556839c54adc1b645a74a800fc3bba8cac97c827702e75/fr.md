```
open(f::Function, command, args...; kwargs...)
```

Semblable à `open(command, args...; kwargs...)`, mais appelle `f(stream)` sur le flux de processus résultant, puis ferme le flux d'entrée et attend que le processus se termine. Retourne la valeur renvoyée par `f` en cas de succès. Lève une erreur si le processus échoue, ou si le processus tente d'imprimer quoi que ce soit sur stdout.
