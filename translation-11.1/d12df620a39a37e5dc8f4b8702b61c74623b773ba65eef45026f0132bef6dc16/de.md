```
Core.memoryrefget(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Gibt den Wert zurück, der im `MemoryRef` gespeichert ist, und wirft einen `BoundsError`, wenn der `Memory` leer ist. Siehe `ref[]`. Die angegebene Speicheranordnung muss mit dem `isatomic`-Parameter kompatibel sein.

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.

