```
Union{}
```

`Union{}`, l'[`Union`](@ref) vide de types, est le type qui n'a pas de valeurs. C'est-à-dire qu'il a la propriété définissante `isa(x, Union{}) == false` pour tout `x`. `Base.Bottom` est défini comme son alias et le type de `Union{}` est `Core.TypeofBottom`.

# Exemples

```jldoctest
julia> isa(nothing, Union{})
false
```
