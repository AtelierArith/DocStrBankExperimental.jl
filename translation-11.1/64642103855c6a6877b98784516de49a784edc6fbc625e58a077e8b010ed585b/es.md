```
checkbounds(Bool, A, I...)
```

Devuelve `true` si los índices especificados `I` están dentro de los límites para el array dado `A`. Los subtipos de `AbstractArray` deben especializar este método si necesitan proporcionar comportamientos personalizados de verificación de límites; sin embargo, en muchos casos se puede confiar en los índices de `A` y en [`checkindex`](@ref).

Véase también [`checkindex`](@ref).

# Ejemplos

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
