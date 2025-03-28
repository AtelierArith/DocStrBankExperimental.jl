```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

Wie [`getindex`](@ref), aber gibt eine Ansicht in den übergeordneten String `s` im Bereich `i:j` oder `r` zurück, anstatt eine Kopie zu erstellen.

Das [`@views`](@ref) Makro konvertiert alle String-Slices `s[i:j]` in Substrings `SubString(s, i, j)` in einem Codeblock.

# Beispiele

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
