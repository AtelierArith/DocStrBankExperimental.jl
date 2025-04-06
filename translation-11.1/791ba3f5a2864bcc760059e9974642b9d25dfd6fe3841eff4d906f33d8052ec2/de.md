```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

Finde das erste Vorkommen von `pattern` in `string`. Entspricht [`findnext(pattern, string, firstindex(s))`](@ref).

# Beispiele

```jldoctest
julia> findfirst("z", "Hello to the world") # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> findfirst("Julia", "JuliaLang")
1:5
```
