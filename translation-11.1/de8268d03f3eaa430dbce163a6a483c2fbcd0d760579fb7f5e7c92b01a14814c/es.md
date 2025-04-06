```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

Llama a `realloc` de la biblioteca estándar de C.

Consulta la advertencia en la documentación de [`free`](@ref) sobre el uso de esto solo en memoria obtenida originalmente de [`malloc`](@ref).
