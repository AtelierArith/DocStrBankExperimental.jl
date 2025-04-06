```
SubstitutionString(substr) <: AbstractString
```

Speichert den gegebenen String `substr` als `SubstitutionString`, zur Verwendung in regulären Ausdrucksersetzungen. Am häufigsten wird es mit dem [`@s_str`](@ref) Makro erstellt.

# Beispiele

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```
