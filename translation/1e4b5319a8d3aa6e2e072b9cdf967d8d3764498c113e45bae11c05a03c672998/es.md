```
Union{}
```

`Union{}`, el vacío [`Union`](@ref) de tipos, es el tipo que no tiene valores. Es decir, tiene la propiedad definitoria `isa(x, Union{}) == false` para cualquier `x`. `Base.Bottom` se define como su alias y el tipo de `Union{}` es `Core.TypeofBottom`.

# Ejemplos

```jldoctest
julia> isa(nothing, Union{})
false
```
