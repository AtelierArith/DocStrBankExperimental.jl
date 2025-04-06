```
withenv(f, kv::Pair...)
```

Ejecuta `f` en un entorno que se modifica temporalmente (no se reemplaza como en `setenv`) por cero o más argumentos `"var"=>val` `kv`. `withenv` se utiliza generalmente a través de la sintaxis `withenv(kv...) do ... end`. Un valor de `nothing` se puede usar para desactivar temporalmente una variable de entorno (si está configurada). Cuando `withenv` retorna, el entorno original ha sido restaurado.

!!! warning
    Cambiar el entorno no es seguro para hilos. Para ejecutar comandos externos con un entorno diferente al del proceso padre, se prefiere usar [`addenv`](@ref) sobre `withenv`.

