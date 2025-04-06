```
imag(A::AbstractArray)
```

Devuelve un array que contiene la parte imaginaria de cada entrada en el array `A`.

Equivalente a `imag.(A)`, excepto que cuando `A` tiene cero dimensiones, se devuelve un array de 0 dimensiones (en lugar de un escalar).

# Ejemplos

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-dimensional Array{Int64, 0}:
-1
```
