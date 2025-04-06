```
axes(A)
```

Devuelve la tupla de índices válidos para el arreglo `A`.

Véase también: [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Ejemplos

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
