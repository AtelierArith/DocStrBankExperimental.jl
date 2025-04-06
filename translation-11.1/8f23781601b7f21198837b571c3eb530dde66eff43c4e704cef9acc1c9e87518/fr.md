```
fieldnames(x::DataType)
```

Obtenez un tuple avec les noms des champs d'un `DataType`.

Voir aussi [`propertynames`](@ref), [`hasfield`](@ref).

# Exemples

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
