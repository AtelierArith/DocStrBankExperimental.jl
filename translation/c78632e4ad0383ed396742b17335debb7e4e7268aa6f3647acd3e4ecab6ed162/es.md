```
read(io::IO, T)
```

Lee un solo valor del tipo `T` desde `io`, en representación binaria canónica.

Ten en cuenta que Julia no convierte el orden de los bytes por ti. Usa [`ntoh`](@ref) o [`ltoh`](@ref) para este propósito.

```
read(io::IO, String)
```

Lee la totalidad de `io`, como un `String` (ver también [`readchomp`](@ref)).

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (categoría Lu: Letra, mayúscula)

julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, String)
"JuliaLang is a GitHub organization"
```
