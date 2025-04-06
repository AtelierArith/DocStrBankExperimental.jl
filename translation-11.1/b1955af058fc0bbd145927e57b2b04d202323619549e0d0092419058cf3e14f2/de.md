```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

Gibt `true` zurück, wenn `s` mit `suffix` endet, das ein String, ein Zeichen oder ein Tupel/Vektor/Menge von Zeichen sein kann. Wenn `suffix` ein Tupel/Vektor/Menge von Zeichen ist, wird getestet, ob das letzte Zeichen von `s` zu dieser Menge gehört.

Siehe auch [`startswith`](@ref), [`contains`](@ref).

# Beispiele

```jldoctest
julia> endswith("Sunday", "day")
true
```
