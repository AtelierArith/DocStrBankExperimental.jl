```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

Retourne `true` si `s` commence par `prefix`, qui peut être une chaîne de caractères, un caractère, ou un tuple/vecteur/ensemble de caractères. Si `prefix` est un tuple/vecteur/ensemble de caractères, teste si le premier caractère de `s` appartient à cet ensemble.

Voir aussi [`endswith`](@ref), [`contains`](@ref).

# Exemples

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
