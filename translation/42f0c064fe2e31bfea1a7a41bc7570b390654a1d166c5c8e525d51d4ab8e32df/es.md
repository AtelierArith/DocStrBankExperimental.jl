```
rot!(n, X, incx, Y, incy, c, s)
```

Sobrescribe `X` con `c*X + s*Y` y `Y` con `-conj(s)*X + c*Y` para los primeros `n` elementos del arreglo `X` con paso `incx` y los primeros `n` elementos del arreglo `Y` con paso `incy`. Devuelve `X` y `Y`.

!!! compat "Julia 1.5"
    `rot!` requiere al menos Julia 1.5.

