```
Core.memoryrefget(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Devuelve el valor almacenado en el `MemoryRef`, lanzando un `BoundsError` si la `Memory` está vacía. Ver `ref[]`. El orden de memoria especificado debe ser compatible con el parámetro `isatomic`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.

