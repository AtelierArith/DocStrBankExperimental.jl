```
Date(d::AbstractString, format::AbstractString; locale="english") -> Date
```

Construye un `Date` analizando la cadena de fecha `d` siguiendo el patrón dado en la cadena `format` (ver [`DateFormat`](@ref) para la sintaxis).

!!! note
    Este método crea un objeto `DateFormat` cada vez que se llama. Se recomienda que crees un objeto [`DateFormat`](@ref) en su lugar y lo uses como el segundo argumento para evitar la pérdida de rendimiento al usar el mismo formato repetidamente.


# Ejemplos

```jldoctest
julia> Date("2020-01-01", "yyyy-mm-dd")
2020-01-01

julia> a = ("2020-01-01", "2020-01-02");

julia> [Date(d, dateformat"yyyy-mm-dd") for d ∈ a] # preferido
2-element Vector{Date}:
 2020-01-01
 2020-01-02
```
