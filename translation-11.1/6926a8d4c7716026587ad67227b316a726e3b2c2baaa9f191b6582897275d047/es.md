```
clear_malloc_data()
```

Limpia cualquier dato de asignación de memoria almacenado al ejecutar julia con `--track-allocation`. Ejecuta el/los comando(s) que deseas probar (para forzar la compilación JIT), luego llama a [`clear_malloc_data`](@ref). Luego ejecuta tu(s) comando(s) nuevamente, cierra Julia y examina los archivos `*.mem` resultantes.
