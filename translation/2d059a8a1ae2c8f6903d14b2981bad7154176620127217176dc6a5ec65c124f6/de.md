```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

Gibt `true` zurück, wenn `s` mit `prefix` beginnt, das ein String, ein Zeichen oder ein Tupel/Vektor/Menge von Zeichen sein kann. Wenn `prefix` ein Tupel/Vektor/Menge von Zeichen ist, wird getestet, ob das erste Zeichen von `s` zu dieser Menge gehört.

Siehe auch [`endswith`](@ref), [`contains`](@ref).

# Beispiele

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
