```
clear!(syms, pids=workers(); mod=Main)
```

Limpia las vinculaciones globales en los módulos inicializándolas a `nothing`. `syms` debe ser de tipo [`Symbol`](@ref) o una colección de `Symbol`s. `pids` y `mod` identifican los procesos y el módulo en el que se deben reinicializar las variables globales. Solo se limpian aquellos nombres que se encuentran definidos bajo `mod`.

Se genera una excepción si se solicita limpiar una constante global.
