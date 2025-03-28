```
dotu(n, X, incx, Y, incy)
```

Función Dot para dos vectores complejos que constan de `n` elementos del arreglo `X` con paso `incx` y `n` elementos del arreglo `Y` con paso `incy`.

# Ejemplos

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
