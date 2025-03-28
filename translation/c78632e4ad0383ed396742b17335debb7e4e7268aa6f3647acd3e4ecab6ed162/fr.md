```
read(io::IO, T)
```

Lire une seule valeur de type `T` à partir de `io`, dans une représentation binaire canonique.

Notez que Julia ne convertit pas l'endianness pour vous. Utilisez [`ntoh`](@ref) ou [`ltoh`](@ref) à cet effet.

```
read(io::IO, String)
```

Lire l'intégralité de `io`, en tant que `String` (voir aussi [`readchomp`](@ref)).

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (catégorie Lu: Lettre, majuscule)

julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, String)
"JuliaLang is a GitHub organization"
```
