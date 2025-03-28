```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

Analysiert Fluchtinformationen in `ir`:

  * `nargs`: die Anzahl der tatsächlichen Argumente des analysierten Aufrufs
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}`: ruft zwischengespeicherte Fluchtinformationen für Argumente ab
