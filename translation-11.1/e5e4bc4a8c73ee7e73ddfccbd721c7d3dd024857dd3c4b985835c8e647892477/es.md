```
versioninfo(io::IO=stdout; verbose::Bool=false)
```

Imprime información sobre la versión de Julia en uso. La salida se controla con argumentos de palabra clave booleanos:

  * `verbose`: imprime toda la información adicional

!!! warning
    La salida de esta función puede contener información sensible. Antes de compartir la salida, revise la salida y elimine cualquier dato que no deba compartirse públicamente.


Véase también: [`VERSION`](@ref).
