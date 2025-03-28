```
isassigned(array, i) -> Bool
```

Prueba si el array dado tiene un valor asociado con el índice `i`. Devuelve `false` si el índice está fuera de límites, o tiene una referencia indefinida.

# Ejemplos

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
