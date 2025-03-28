```
keys(m::RegexMatch) -> Vector
```

Renvoie un vecteur de clés pour tous les groupes de capture de l'expression régulière sous-jacente. Une clé est incluse même si le groupe de capture ne correspond pas. C'est-à-dire que `idx` sera dans la valeur de retour même si `m[idx] == nothing`.

Les groupes de capture non nommés auront des clés entières correspondant à leur index. Les groupes de capture nommés auront des clés de chaîne.

!!! compat "Julia 1.7"
    Cette méthode a été ajoutée dans Julia 1.7


# Exemples

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
