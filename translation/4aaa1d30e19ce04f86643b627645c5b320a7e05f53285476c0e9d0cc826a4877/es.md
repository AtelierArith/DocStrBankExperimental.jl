```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

Construye un `Time` analizando la cadena de fecha y hora `t` siguiendo el patrón dado en el objeto [`DateFormat`](@ref), o dateformat"HH:MM:SS.s" si se omite.

Similar a `Time(::AbstractString, ::AbstractString)` pero más eficiente al analizar repetidamente cadenas de tiempo con formato similar con un objeto `DateFormat` precreado.
