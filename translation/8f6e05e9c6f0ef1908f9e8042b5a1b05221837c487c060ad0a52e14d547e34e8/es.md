```
conj(A::AbstractArray)
```

Devuelve un array que contiene el conjugado complejo de cada entrada en el array `A`.

Equivalente a `conj.(A)`, excepto que cuando `eltype(A) <: Real` `A` se devuelve sin copiar, y que cuando `A` tiene cero dimensiones, se devuelve un array de 0 dimensiones (en lugar de un escalar).

# Ejemplos

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-dimensional Array{Complex{Int64}, 0}:
2 + 1im
```
