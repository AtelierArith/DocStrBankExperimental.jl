```
findlast(ch::AbstractChar, string::AbstractString)
```

Encuentra la última ocurrencia del carácter `ch` en `string`.

!!! compat "Julia 1.3"
    Este método requiere al menos Julia 1.3.


# Ejemplos

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
