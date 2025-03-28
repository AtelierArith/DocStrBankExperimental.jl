```
setindex!(A, X, inds...)
A[inds...] = X
```

Almacena valores del arreglo `X` dentro de un subconjunto de `A` según lo especificado por `inds`. La sintaxis `A[inds...] = X` es equivalente a `(setindex!(A, X, inds...); X)`.

!!! advertencia
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
