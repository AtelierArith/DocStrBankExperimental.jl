```
circshift!(dest, src, shifts)
```

Desplaza circularmente, es decir, rota, los datos en `src`, almacenando el resultado en `dest`. `shifts` especifica la cantidad a desplazar en cada dimensión.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Véase también [`circshift`](@ref).
