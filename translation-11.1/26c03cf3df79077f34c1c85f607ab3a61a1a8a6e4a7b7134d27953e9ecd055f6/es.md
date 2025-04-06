```
prevfloat(x::AbstractFloat)
```

Devuelve el número de punto flotante más grande `y` del mismo tipo que `x` tal que `y < x`. Si no existe tal `y` (por ejemplo, si `x` es `-Inf` o `NaN`), entonces devuelve `x`.
