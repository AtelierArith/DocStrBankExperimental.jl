```
startswith(s::AbstractString, prefix::Regex)
```

Retourne `true` si `s` commence par le motif regex, `prefix`.

!!! note
    `startswith` ne compile pas l'ancrage dans l'expression régulière, mais passe plutôt l'ancrage comme `match_option` à PCRE. Si le temps de compilation est amorti, `occursin(r"^...", s)` est plus rapide que `startswith(s, r"...")`.


Voir aussi [`occursin`](@ref) et [`endswith`](@ref).

!!! compat "Julia 1.2"
    Cette méthode nécessite au moins Julia 1.2.


# Exemples

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
