```
foldr(op, itr; [init])
```

Como [`reduce`](@ref), pero con asociatividad a la derecha garantizada. Si se proporciona, el argumento clave `init` se utilizará exactamente una vez. En general, será necesario proporcionar `init` para trabajar con colecciones vacías.

# Ejemplos

```jldoctest
julia> foldr(=>, 1:4)
1 => (2 => (3 => 4))

julia> foldr(=>, 1:4; init=0)
1 => (2 => (3 => (4 => 0)))
```
