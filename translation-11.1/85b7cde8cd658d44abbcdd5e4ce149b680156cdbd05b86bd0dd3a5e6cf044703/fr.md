```
SubstitutionString(substr) <: AbstractString
```

Stocke la chaîne donnée `substr` en tant que `SubstitutionString`, pour une utilisation dans les substitutions d'expressions régulières. Construit le plus souvent à l'aide du macro [`@s_str`](@ref).

# Exemples

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```
