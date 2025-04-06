```
Regex(pattern[, flags]) <: AbstractPattern
```

Un tipo que representa una expresión regular. Los objetos `Regex` se pueden usar para hacer coincidir cadenas con [`match`](@ref).

Los objetos `Regex` se pueden crear utilizando el macro de cadena [`@r_str`](@ref). El constructor `Regex(pattern[, flags])` se utiliza generalmente si la cadena `pattern` necesita ser interpolada. Consulte la documentación del macro de cadena para obtener detalles sobre las banderas.

!!! nota
    Para escapar variables interpoladas, use `\Q` y `\E` (por ejemplo, `Regex("\\Q$x\\E")`)

