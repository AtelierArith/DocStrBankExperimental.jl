```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

Finde das nächste Vorkommen von `pattern` in `string`, beginnend an der Position `start`. `pattern` kann entweder eine Zeichenkette oder ein regulärer Ausdruck sein, in diesem Fall muss `string` vom Typ `String` sein.

Der Rückgabewert ist ein Bereich von Indizes, an dem die übereinstimmende Sequenz gefunden wird, so dass `s[findnext(x, s, i)] == x`:

`findnext("substring", string, i)` == `start:stop`, so dass `string[start:stop] == "substring"` und `i <= start`, oder `nothing`, wenn keine Übereinstimmung gefunden wurde.

# Beispiele

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
