```
fieldnames(x::DataType)
```

Bir `DataType`'in alan adlarını içeren bir demet alır.

Ayrıca bkz. [`propertynames`](@ref), [`hasfield`](@ref).

# Örnekler

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
