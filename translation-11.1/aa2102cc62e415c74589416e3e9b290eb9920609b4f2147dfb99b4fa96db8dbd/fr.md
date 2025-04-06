```
findlast(pattern::AbstractString, string::AbstractString)
```

Trouver la dernière occurrence de `pattern` dans `string`. Équivalent à [`findprev(pattern, string, lastindex(string))`](@ref).

# Exemples

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
