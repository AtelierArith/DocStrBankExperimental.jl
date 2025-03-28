```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

Recherche de toutes les correspondances de l'expression régulière `r` dans `s` et retourne un itérateur sur les correspondances. Si `overlap` est `true`, les séquences correspondantes peuvent se chevaucher dans les indices de la chaîne d'origine, sinon elles doivent provenir de plages de caractères distinctes.

# Exemples

```jldoctest
julia> rx = r"a.a"
r"a.a"

julia> m = eachmatch(rx, "a1a2a3a")
Base.RegexMatchIterator{String}(r"a.a", "a1a2a3a", false)

julia> collect(m)
2-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a3a")

julia> collect(eachmatch(rx, "a1a2a3a", overlap = true))
3-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a2a")
 RegexMatch("a3a")
```
