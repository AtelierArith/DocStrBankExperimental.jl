```
Core.memoryrefset!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Almacena el valor en el `MemoryRef`, lanzando un `BoundsError` si la `Memory` está vacía. Ver `ref[] = value`. El orden de memoria especificado debe ser compatible con el parámetro `isatomic`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.

