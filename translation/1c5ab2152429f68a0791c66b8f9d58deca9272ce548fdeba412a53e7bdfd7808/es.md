```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Intersecar todos los conjuntos pasados y sobrescribir `s` con el resultado. Mantener el orden con arreglos.

!!! advertencia
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

