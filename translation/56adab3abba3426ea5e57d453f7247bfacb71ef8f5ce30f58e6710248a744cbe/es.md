```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

Encuentra la siguiente ocurrencia del carácter `ch` en `string` comenzando en la posición `start`.

!!! compat "Julia 1.3"
    Este método requiere al menos Julia 1.3.


# Ejemplos

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
