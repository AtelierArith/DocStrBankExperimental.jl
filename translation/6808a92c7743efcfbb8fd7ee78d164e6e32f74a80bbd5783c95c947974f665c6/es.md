```
Módulo
```

Un `Módulo` es un espacio de trabajo de variables globales separado. Consulta [`module`](@ref) y la [sección del manual sobre módulos](@ref modules) para más detalles.

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

Devuelve un módulo con el nombre especificado. Un `baremodule` corresponde a `Module(:ModuleName, false)`

Se puede crear un módulo vacío que no contenga nombres en absoluto con `Module(:ModuleName, false, false)`. Este módulo no importará `Base` ni `Core` y no contiene una referencia a sí mismo.
