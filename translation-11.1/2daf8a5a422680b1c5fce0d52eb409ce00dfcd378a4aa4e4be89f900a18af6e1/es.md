```
CFunction struct
```

Manejador de recolección de basura para el valor de retorno de `@cfunction` cuando el primer argumento está anotado con '$'. Como todos los manejadores de `cfunction`, debe ser pasado a `ccall` como un `Ptr{Cvoid}`, y se convertirá automáticamente en el sitio de llamada al tipo apropiado.

Consulta [`@cfunction`](@ref).
