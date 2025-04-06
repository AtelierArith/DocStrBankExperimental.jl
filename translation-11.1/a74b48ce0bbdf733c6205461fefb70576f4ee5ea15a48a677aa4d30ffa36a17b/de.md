```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

Wenden Sie ein printf-Formatobjekt `f` auf die bereitgestellten `args` an und geben Sie die formatierte Zeichenfolge zurück (1. Methode) oder drucken Sie direkt auf ein `io`-Objekt (2. Methode). Siehe [`@printf`](@ref) für weitere Details zur Unterstützung von C `printf`.
