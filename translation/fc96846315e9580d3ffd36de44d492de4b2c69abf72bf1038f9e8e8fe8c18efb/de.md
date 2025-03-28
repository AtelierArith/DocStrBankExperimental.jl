```
Core.memoryrefset!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Speichert den Wert im `MemoryRef` und wirft einen `BoundsError`, wenn der `Memory` leer ist. Siehe `ref[] = value`. Die angegebene Speicheranordnung muss mit dem Parameter `isatomic` kompatibel sein.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.

