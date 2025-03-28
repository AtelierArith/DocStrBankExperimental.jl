```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

Supprime les premiers `head` et les derniers `tail` caractères de `s`. L'appel `chop(s)` supprime le dernier caractère de `s`. S'il est demandé de supprimer plus de caractères que `length(s)`, alors une chaîne vide est renvoyée.

Voir aussi [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref).

# Exemples

```jldoctest
julia> a = "Mars"
"Mars"

julia> chop(a)
"Mar"

julia> chop(a, head = 1, tail = 2)
"ar"

julia> chop(a, head = 5, tail = 5)
""
```
