```
Time(t::AbstractString, format::AbstractString; locale="english") -> Time
```

Construye un `Time` analizando la cadena de tiempo `t` siguiendo el patrón dado en la cadena `format` (ver [`DateFormat`](@ref) para la sintaxis).

!!! note
    Este método crea un objeto `DateFormat` cada vez que se llama. Se recomienda que crees un objeto [`DateFormat`](@ref) en su lugar y lo uses como el segundo argumento para evitar la pérdida de rendimiento al usar el mismo formato repetidamente.


# Ejemplos

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # preferido
2-element Vector{Time}:
 12:34:00
 02:34:00
```
