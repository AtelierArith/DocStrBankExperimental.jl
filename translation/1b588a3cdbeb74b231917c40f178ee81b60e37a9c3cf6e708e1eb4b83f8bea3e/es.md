```
Función
```

Tipo abstracto de todas las funciones.

# Ejemplos

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (tipo singleton de la función sin, subtipo de Function)

julia> ans <: Function
true
```
