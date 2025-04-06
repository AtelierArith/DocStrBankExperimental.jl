```
fetch(;include_meta = true) -> data
```

Devuelve una copia del búfer de perfiles de backtraces. Ten en cuenta que los valores en `data` solo tienen significado en esta máquina en la sesión actual, porque dependen de las direcciones de memoria exactas utilizadas en la compilación JIT. Esta función es principalmente para uso interno; [`retrieve`](@ref) puede ser una mejor opción para la mayoría de los usuarios. Por defecto, se incluye metadatos como threadid y taskid. Establece `include_meta` en `false` para eliminar los metadatos.
