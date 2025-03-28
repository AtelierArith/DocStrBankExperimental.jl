```
fieldnames(x::DataType)
```

Obtiene una tupla con los nombres de los campos de un `DataType`.

Véase también [`propertynames`](@ref), [`hasfield`](@ref).

# Ejemplos

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
