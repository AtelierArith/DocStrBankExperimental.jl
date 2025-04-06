```
isvalid(s::AbstractString, i::Integer) -> Bool
```

Prädikat, das angibt, ob der gegebene Index der Beginn der Kodierung eines Zeichens in `s` ist oder nicht. Wenn `isvalid(s, i)` wahr ist, dann gibt `s[i]` das Zeichen zurück, dessen Kodierung an diesem Index beginnt; wenn es falsch ist, wird `s[i]` einen ungültigen Indexfehler oder einen Bereichsfehler auslösen, abhängig davon, ob `i` im Bereich liegt. Damit `isvalid(s, i)` eine O(1)-Funktion sein kann, muss die Kodierung von `s` [selbstsynchronisierend](https://en.wikipedia.org/wiki/Self-synchronizing_code) sein. Dies ist eine grundlegende Annahme der generischen Zeichenfolgenunterstützung von Julia.

Siehe auch [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref).

# Beispiele

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> isvalid(str, 2)
false

julia> str[2]
ERROR: StringIndexError: ungültiger Index [2], gültige benachbarte Indizes [1]=>'α', [3]=>'β'
Stacktrace:
[...]
```
