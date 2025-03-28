```
real(A::AbstractArray)
```

Devuelve un array que contiene la parte real de cada entrada en el array `A`.

Equivalente a `real.(A)`, excepto que cuando `eltype(A) <: Real` `A` se devuelve sin copiar, y que cuando `A` tiene cero dimensiones, se devuelve un array de 0 dimensiones (en lugar de un escalar).

# Ejemplos

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-dimensional Array{Int64, 0}:
2
```
