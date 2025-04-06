```
dot(n, X, incx, Y, incy)
```

Producto punto de dos vectores que consisten en `n` elementos del arreglo `X` con paso `incx` y `n` elementos del arreglo `Y` con paso `incy`.

# Ejemplos

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
