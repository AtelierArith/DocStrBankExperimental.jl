```
eval(expr)
```

Évalue une expression dans le scope global du module contenant. Chaque `Module` (sauf ceux définis avec `baremodule`) a sa propre définition à un argument de `eval`, qui évalue les expressions dans ce module.
