```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Prueba si una colección está en orden clasificado. Las palabras clave modifican qué orden se considera clasificado, como se describe en la documentación de [`sort!`](@ref).

# Ejemplos

```jldoctest
julia> issorted([1, 2, 3])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
false

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
true

julia> issorted([1, 2, -2, 3], by=abs)
true
```
