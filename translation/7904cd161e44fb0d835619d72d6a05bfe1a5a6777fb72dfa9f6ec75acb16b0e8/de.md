```
isassigned(array, i) -> Bool
```

Überprüfen Sie, ob das gegebene Array einen Wert mit dem Index `i` hat. Gibt `false` zurück, wenn der Index außerhalb der Grenzen liegt oder eine undefinierte Referenz hat.

# Beispiele

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
