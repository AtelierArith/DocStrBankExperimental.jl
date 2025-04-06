```
DateTime(dt::AbstractString, df::DateFormat=ISODateTimeFormat) -> DateTime
```

Construye un `DateTime` analizando la cadena de fecha y hora `dt` siguiendo el patrón dado en el objeto [`DateFormat`](@ref), o dateformat"yyyy-mm-dd\THH:MM:SS.s" si se omite.

Similar a `DateTime(::AbstractString, ::AbstractString)` pero más eficiente al analizar repetidamente cadenas de fecha y hora con un formato similar utilizando un objeto `DateFormat` precreado.
