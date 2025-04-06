```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

Como [`asyncmap`](@ref), pero almacena la salida en `results` en lugar de devolver una colección.

!!! advertencia
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

