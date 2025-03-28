```
SubstitutionString(substr) <: AbstractString
```

Almacena la cadena dada `substr` como un `SubstitutionString`, para su uso en sustituciones de expresiones regulares. Comúnmente construido utilizando el macro [`@s_str`](@ref).

# Ejemplos

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```
