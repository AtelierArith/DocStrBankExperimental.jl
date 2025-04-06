```
size(A::AbstractArray, [dim])
```

Devuelve una tupla que contiene las dimensiones de `A`. Opcionalmente, puedes especificar una dimensión para obtener solo la longitud de esa dimensión.

Ten en cuenta que `size` puede no estar definido para arreglos con índices no estándar, en cuyo caso [`axes`](@ref) puede ser útil. Consulta el capítulo del manual sobre [arreglos con índices personalizados](@ref man-custom-indices).

Véase también: [`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref).

# Ejemplos

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
