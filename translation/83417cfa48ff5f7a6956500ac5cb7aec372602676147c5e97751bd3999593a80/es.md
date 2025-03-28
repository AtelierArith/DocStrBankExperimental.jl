```
LinearAlgebra.checksquare(A)
```

Verifica que una matriz sea cuadrada y luego devuelve su dimensión común. Para múltiples argumentos, devuelve un vector.

# Ejemplos

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
