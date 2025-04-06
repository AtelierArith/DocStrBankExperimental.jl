```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

Überprüfen, ob ein Zeichen zum ASCII-Zeichensatz gehört oder ob dies für alle Elemente eines Strings zutrifft.

# Beispiele

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

Zum Beispiel kann `isascii` als Prädikatsfunktion für [`filter`](@ref) oder [`replace`](@ref) verwendet werden, um nicht-ASCII-Zeichen zu entfernen oder zu ersetzen:

```jldoctest
julia> filter(isascii, "abcdeγfgh") # nicht-ASCII-Zeichen verwerfen
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # nicht-ASCII-Zeichen durch Leerzeichen ersetzen
"abcde fgh"
```
