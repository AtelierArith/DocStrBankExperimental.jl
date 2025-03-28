```
RegexMatch <: AbstractMatch
```

Un tipo que representa una coincidencia única a un [`Regex`](@ref) encontrada en una cadena. Típicamente creado a partir de la función [`match`](@ref).

El campo `match` almacena la subcadena de la cadena completa coincidente. El campo `captures` almacena las subcadenas para cada grupo de captura, indexadas por número. Para indexar por nombre de grupo de captura, el objeto de coincidencia completo debe ser indexado en su lugar, como se muestra en los ejemplos. La ubicación del inicio de la coincidencia se almacena en el campo `offset`. El campo `offsets` almacena las ubicaciones del inicio de cada grupo de captura, con 0 denotando un grupo que no fue capturado.

Este tipo se puede usar como un iterador sobre los grupos de captura del `Regex`, produciendo las subcadenas capturadas en cada grupo. Debido a esto, las capturas de una coincidencia pueden ser desestructuradas. Si un grupo no fue capturado, se producirá `nothing` en lugar de una subcadena.

Los métodos que aceptan un objeto `RegexMatch` están definidos para [`iterate`](@ref), [`length`](@ref), [`eltype`](@ref), [`keys`](@ref keys(::RegexMatch)), [`haskey`](@ref), y [`getindex`](@ref), donde las claves son los nombres o números de un grupo de captura. Consulte [`keys`](@ref keys(::RegexMatch)) para más información.

# Ejemplos

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # desestructurar grupos de captura por iteración

julia> hr
"11"
```
