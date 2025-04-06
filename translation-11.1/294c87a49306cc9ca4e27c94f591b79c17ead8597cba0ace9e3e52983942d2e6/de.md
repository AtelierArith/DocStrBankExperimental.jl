```
lowercase(c::AbstractChar)
```

Konvertiere `c` in Kleinbuchstaben.

Siehe auch [`uppercase`](@ref), [`titlecase`](@ref).

# Beispiele

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```
