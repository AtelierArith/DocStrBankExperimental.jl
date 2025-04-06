```
Symbol(x...) -> Symbol
```

Crea un [`Symbol`](@ref) concatenando las representaciones en cadena de los argumentos.

# Ejemplos

```jldoctest
julia> Symbol("my", "name")
:myname

julia> Symbol("day", 4)
:day4
```
