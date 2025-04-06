```
symdiff!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Construye la diferencia simétrica de los conjuntos pasados y sobrescribe `s` con el resultado. Cuando `s` es un arreglo, se mantiene el orden. Ten en cuenta que en este caso la multiplicidad de los elementos es importante.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

