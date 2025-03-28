```
CFunction-Struktur
```

Garbage-Collection-Handle für den Rückgabewert von `@cfunction`, wenn das erste Argument mit '$' annotiert ist. Wie alle `cfunction`-Handles sollte es als `Ptr{Cvoid}` an `ccall` übergeben werden und wird am Aufrufort automatisch in den entsprechenden Typ konvertiert.

Siehe [`@cfunction`](@ref).
