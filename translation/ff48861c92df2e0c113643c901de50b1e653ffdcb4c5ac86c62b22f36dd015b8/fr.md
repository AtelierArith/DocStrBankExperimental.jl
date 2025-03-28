```
istextmime(m::MIME)
```

Déterminez si un type MIME est des données textuelles. Les types MIME sont supposés être des données binaires, sauf pour un ensemble de types connus pour être des données textuelles (possiblement Unicode).

# Exemples

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
