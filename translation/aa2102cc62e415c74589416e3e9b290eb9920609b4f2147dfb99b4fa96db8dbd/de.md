```
findlast(pattern::AbstractString, string::AbstractString)
```

Finde das letzte Vorkommen von `pattern` in `string`. Entspricht [`findprev(pattern, string, lastindex(string))`](@ref).

# Beispiele

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
