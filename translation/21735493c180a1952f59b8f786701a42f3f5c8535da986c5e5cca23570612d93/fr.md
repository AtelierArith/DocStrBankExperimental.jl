```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

Analyse les informations d'échappement dans `ir` :

  * `nargs` : le nombre d'arguments réels de l'appel analysé
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}` : récupère les informations d'échappement des arguments mises en cache
