```
peek(stream[, T=UInt8])
```

Lese und gebe einen Wert des Typs `T` aus einem Stream zurück, ohne die aktuelle Position im Stream zu verschieben. Siehe auch [`startswith(stream, char_or_string)`](@ref).

# Beispiele

```jldoctest
julia> b = IOBuffer("julia");

julia> peek(b)
0x6a

julia> position(b)
0

julia> peek(b, Char)
'j': ASCII/Unicode U+006A (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```

!!! compat "Julia 1.5"
    Die Methode, die einen Typ akzeptiert, erfordert Julia 1.5 oder höher.

