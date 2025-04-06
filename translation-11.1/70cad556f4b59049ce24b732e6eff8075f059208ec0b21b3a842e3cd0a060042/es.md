```
getfield(value, name::Symbol, [order::Symbol])
getfield(value, i::Int, [order::Symbol])
```

Extrae un campo de un `value` compuesto por nombre o posición. Opcionalmente, se puede definir un orden para la operación. Si el campo fue declarado `@atomic`, se recomienda encarecidamente que la especificación sea compatible con los almacenes en esa ubicación. De lo contrario, si no se declara como `@atomic`, este parámetro debe ser `:not_atomic` si se especifica. Ver también [`getproperty`](@ref Base.getproperty) y [`fieldnames`](@ref).

# Ejemplos

```jldoctest
julia> a = 1//2
1//2

julia> getfield(a, :num)
1

julia> a.num
1

julia> getfield(a, 1)
1
```
