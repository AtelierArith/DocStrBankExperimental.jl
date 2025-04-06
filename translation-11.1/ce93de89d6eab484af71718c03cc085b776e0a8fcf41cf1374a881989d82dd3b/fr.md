```
endswith(s::AbstractString, suffix::Regex)
```

Retourne `true` si `s` se termine par le motif regex, `suffix`.

!!! note
    `endswith` ne compile pas l'ancrage dans l'expression régulière, mais passe plutôt l'ancrage comme `match_option` à PCRE. Si le temps de compilation est amorti, `occursin(r"...$", s)` est plus rapide que `endswith(s, r"...")`.


Voir aussi [`occursin`](@ref) et [`startswith`](@ref).

!!! compat "Julia 1.2"
    Cette méthode nécessite au moins Julia 1.2.


# Exemples

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
