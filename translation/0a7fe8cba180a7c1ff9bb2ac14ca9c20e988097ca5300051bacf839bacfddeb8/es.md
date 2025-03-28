```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

Prueba si una variable global o un campo de objeto está definido. Los argumentos pueden ser un módulo y un símbolo o un objeto compuesto y el nombre del campo (como un símbolo) o índice. Opcionalmente, se puede definir un orden para la operación. Si el campo fue declarado `@atomic`, se recomienda encarecidamente que la especificación sea compatible con las asignaciones a esa ubicación. De lo contrario, si no se declara como `@atomic`, este parámetro debe ser `:not_atomic` si se especifica.

Para probar si un elemento de un arreglo está definido, utiliza [`isassigned`](@ref) en su lugar.

Ver también [`@isdefined`](@ref).

# Ejemplos

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
