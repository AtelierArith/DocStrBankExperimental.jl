```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

Imprime los resultados de perfilado en `io`. Esta variante se utiliza para examinar los resultados exportados por una llamada anterior a [`retrieve`](@ref). Proporcione el vector `data` de trazas de pila y un diccionario `lidict` de información de línea.

Consulte `Profile.print([io], data)` para una explicación de los argumentos de palabra clave válidos.
