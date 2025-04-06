```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

Retourne `true` si `s` se termine par `suffix`, qui peut être une chaîne, un caractère, ou un tuple/vecteur/ensemble de caractères. Si `suffix` est un tuple/vecteur/ensemble de caractères, teste si le dernier caractère de `s` appartient à cet ensemble.

Voir aussi [`startswith`](@ref), [`contains`](@ref).

# Exemples

```jldoctest
julia> endswith("Sunday", "day")
true
```
