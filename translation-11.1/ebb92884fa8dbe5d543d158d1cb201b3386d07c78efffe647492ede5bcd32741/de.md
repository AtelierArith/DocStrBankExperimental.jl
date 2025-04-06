```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

Sucht nach dem ersten Treffer des regulären Ausdrucks `r` in `s` und gibt ein [`RegexMatch`](@ref) Objekt zurück, das den Treffer enthält, oder nichts, wenn der Treffer fehlgeschlagen ist. Der übereinstimmende Teilstring kann durch den Zugriff auf `m.match` abgerufen werden, und die erfassten Sequenzen können durch den Zugriff auf `m.captures` abgerufen werden. Das optionale Argument `idx` gibt einen Index an, an dem die Suche beginnen soll.

# Beispiele

```jldoctest
julia> rx = r"a(.)a"
r"a(.)a"

julia> m = match(rx, "cabac")
RegexMatch("aba", 1="b")

julia> m.captures
1-element Vector{Union{Nothing, SubString{String}}}:
 "b"

julia> m.match
"aba"

julia> match(rx, "cabac", 3) === nothing
true
```
