```
coalesce(x...)
```

Devuelve el primer valor en los argumentos que no es igual a [`missing`](@ref), si lo hay. De lo contrario, devuelve `missing`.

Véase también [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref).

# Ejemplos

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # devuelve `nothing`

julia> coalesce(missing, missing)
missing
```
