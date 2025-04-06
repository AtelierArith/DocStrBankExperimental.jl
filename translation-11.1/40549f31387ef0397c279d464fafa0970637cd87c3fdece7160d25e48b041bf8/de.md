```
ascii(s::AbstractString)
```

Konvertiere einen String in den Typ `String` und überprüfe, ob er nur ASCII-Daten enthält, andernfalls wird ein `ArgumentError` ausgelöst, der die Position des ersten nicht-ASCII-Bytes angibt.

Siehe auch das [`isascii`](@ref) Prädikat, um nicht-ASCII-Zeichen zu filtern oder zu ersetzen.

# Beispiele

```jldoctest
julia> ascii("abcdeγfgh")
ERROR: ArgumentError: invalid ASCII at index 6 in "abcdeγfgh"
Stacktrace:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
