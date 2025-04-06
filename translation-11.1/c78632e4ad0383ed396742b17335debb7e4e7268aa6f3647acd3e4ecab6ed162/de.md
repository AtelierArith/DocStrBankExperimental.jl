```
read(io::IO, T)
```

Lese einen einzelnen Wert des Typs `T` von `io` in kanonischer binärer Darstellung.

Beachte, dass Julia die Endianness nicht für dich konvertiert. Verwende [`ntoh`](@ref) oder [`ltoh`](@ref) zu diesem Zweck.

```
read(io::IO, String)
```

Lese den gesamten Inhalt von `io` als `String` (siehe auch [`readchomp`](@ref)).

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (Kategorie Lu: Buchstabe, groß)

julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation");

julia> read(io, String)
"JuliaLang ist eine GitHub-Organisation"
```
