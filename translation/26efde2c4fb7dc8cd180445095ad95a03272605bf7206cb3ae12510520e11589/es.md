```
dotc(n, X, incx, U, incy)
```

Función Dot para dos vectores complejos, que consiste en `n` elementos del arreglo `X` con paso `incx` y `n` elementos del arreglo `U` con paso `incy`, conjugando el primer vector.

# Ejemplos

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
