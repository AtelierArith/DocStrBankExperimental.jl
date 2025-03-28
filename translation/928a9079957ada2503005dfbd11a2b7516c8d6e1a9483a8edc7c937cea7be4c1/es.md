```
reflect!(x, y, c, s)
```

Sobrescribe `x` con `c*x + s*y` y `y` con `conj(s)*x - c*y`. Devuelve `x` y `y`.

!!! compat "Julia 1.5"
    `reflect!` requiere al menos Julia 1.5.

