```
foldl(op, itr; [init])
```

Como [`reduce`](@ref), pero con asociatividad izquierda garantizada. Si se proporciona, el argumento clave `init` se utilizará exactamente una vez. En general, será necesario proporcionar `init` para trabajar con colecciones vacías.

Véase también [`mapfoldl`](@ref), [`foldr`](@ref), [`accumulate`](@ref).

# Ejemplos

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
