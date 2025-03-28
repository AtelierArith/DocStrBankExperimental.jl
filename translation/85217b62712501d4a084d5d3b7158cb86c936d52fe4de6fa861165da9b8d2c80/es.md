```
lazy"str"
```

Crea un [`LazyString`](@ref) utilizando la sintaxis de interpolación de cadenas regular. Ten en cuenta que las interpolaciones son *evaluadas* en el momento de la construcción de LazyString, pero la *impresión* se retrasa hasta el primer acceso a la cadena.

Consulta la documentación de [`LazyString`](@ref) para conocer las propiedades de seguridad para programas concurrentes.

# Ejemplos

```
julia> n = 5; str = lazy"n es $n"
"n es 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"` requiere Julia 1.8 o posterior.

