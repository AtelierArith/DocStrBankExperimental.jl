```
fieldnames(x::DataType)
```

Erhalten Sie ein Tupel mit den Namen der Felder eines `DataType`.

Siehe auch [`propertynames`](@ref), [`hasfield`](@ref).

# Beispiele

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
