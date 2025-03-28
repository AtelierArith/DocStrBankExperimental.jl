```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Gibt zurück, ob ein Wert im `MemoryRef` gespeichert ist, wobei false zurückgegeben wird, wenn der `Memory` leer ist. Siehe [`isassigned(::Base.RefValue)`](@ref), [`Core.memoryrefget`](@ref). Die angegebene Speicheranordnung muss mit dem `isatomic`-Parameter kompatibel sein.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.

