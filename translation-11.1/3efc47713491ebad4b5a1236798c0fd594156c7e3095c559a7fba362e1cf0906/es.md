```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

Cambia la precisión aritmética de `T` (en la `base` dada) durante la duración de `f`. Es lógicamente equivalente a:

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

A menudo se usa como `setprecision(T, precision) do ... end`

Nota: `nextfloat()`, `prevfloat()` no utilizan la precisión mencionada por `setprecision`.

!!! compat "Julia 1.8"
    La palabra clave `base` requiere al menos Julia 1.8.

