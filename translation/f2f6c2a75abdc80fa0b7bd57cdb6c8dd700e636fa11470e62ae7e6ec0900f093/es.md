```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

Dada una ejecución de perfilado anterior, determina quién llamó a una función particular. Suministrar el nombre del archivo (y opcionalmente, el rango de números de línea sobre los cuales se define la función) te permite desambiguar un método sobrecargado. El valor devuelto es un vector que contiene un conteo del número de llamadas e información de línea sobre el llamador. Se puede suministrar opcionalmente un `data` de backtrace obtenido de [`retrieve`](@ref); de lo contrario, se utiliza el búfer de perfil interno actual.
