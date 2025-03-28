```
DateTime(dt::AbstractString, format::AbstractString; locale="english") -> DateTime
```

Construye un `DateTime` analizando la cadena de fecha y hora `dt` siguiendo el patrón dado en la cadena `format` (ver [`DateFormat`](@ref) para la sintaxis).

!!! note
    Este método crea un objeto `DateFormat` cada vez que se llama. Se recomienda que crees un objeto [`DateFormat`](@ref) en su lugar y lo uses como segundo argumento para evitar la pérdida de rendimiento al usar el mismo formato repetidamente.


# Ejemplos

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # preferido
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
