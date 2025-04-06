```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

Analiza la información de escape en `ir`:

  * `nargs`: el número de argumentos reales de la llamada analizada
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}`: recupera la información de escape de argumento en caché
