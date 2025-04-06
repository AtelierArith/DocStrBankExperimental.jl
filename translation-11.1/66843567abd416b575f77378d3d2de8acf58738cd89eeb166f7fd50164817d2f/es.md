```
Date(d::AbstractString, df::DateFormat=ISODateFormat) -> Date
```

Construye un `Date` analizando la cadena de fecha `d` siguiendo el patrón dado en el objeto [`DateFormat`](@ref), o dateformat"yyyy-mm-dd" si se omite.

Similar a `Date(::AbstractString, ::AbstractString)` pero más eficiente al analizar repetidamente cadenas de fecha con un formato similar con un objeto `DateFormat` precreado.
