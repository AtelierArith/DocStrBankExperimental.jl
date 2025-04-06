```
cumprod!(y::AbstractVector, x::AbstractVector)
```

Producto acumulativo de un vector `x`, almacenando el resultado en `y`. Ver también [`cumprod`](@ref).

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

