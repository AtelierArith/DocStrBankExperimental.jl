```
ispunct(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen zur Unicode-Allgemeinkategorie Interpunktion gehört, d.h. ein Zeichen, dessen Kategoriencode mit 'P' beginnt.

# Beispiele

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
