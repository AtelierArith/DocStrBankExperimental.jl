```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

Devuelve si hay un valor almacenado en el `MemoryRef`, devolviendo falso si la `Memory` está vacía. Consulta [`isassigned(::Base.RefValue)`](@ref), [`Core.memoryrefget`](@ref). El orden de memoria especificado debe ser compatible con el parámetro `isatomic`.

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.

