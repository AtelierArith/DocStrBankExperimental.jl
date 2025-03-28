```
cumprod!(B, A; dims::Integer)
```

Producto acumulativo de `A` a lo largo de la dimensión `dims`, almacenando el resultado en `B`. Ver también [`cumprod`](@ref).

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

