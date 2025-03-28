```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

Trouve la première occurrence de `pattern` dans `string`. Équivalent à [`findnext(pattern, string, firstindex(s))`](@ref).

# Exemples

```jldoctest
julia> findfirst("z", "Hello to the world") # ne retourne rien, mais n'est pas affiché dans le REPL

julia> findfirst("Julia", "JuliaLang")
1:5
```
