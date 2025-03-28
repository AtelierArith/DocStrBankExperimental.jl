```
cumsum!(B, A; dims::Integer)
```

Suma acumulativa de `A` a lo largo de la dimensión `dims`, almacenando el resultado en `B`. Ver también [`cumsum`](@ref).

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

