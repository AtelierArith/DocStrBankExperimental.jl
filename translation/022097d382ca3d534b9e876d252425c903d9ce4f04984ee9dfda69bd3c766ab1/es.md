```
reim(A::AbstractArray)
```

Devuelve una tupla de dos arreglos que contienen respectivamente la parte real y la parte imaginaria de cada entrada en `A`.

Equivalente a `(real.(A), imag.(A))`, excepto que cuando `eltype(A) <: Real` `A` se devuelve sin copiar para representar la parte real, y que cuando `A` tiene cero dimensiones, se devuelve un arreglo de 0 dimensiones (en lugar de un escalar).

# Ejemplos

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
