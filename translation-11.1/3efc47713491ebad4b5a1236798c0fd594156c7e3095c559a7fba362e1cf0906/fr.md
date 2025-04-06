```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

Changez la précision arithmétique de `T` (dans la base donnée) pour la durée de `f`. C'est logiquement équivalent à :

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

Souvent utilisé sous la forme `setprecision(T, precision) do ... end`

Note : `nextfloat()`, `prevfloat()` n'utilisent pas la précision mentionnée par `setprecision`.

!!! compat "Julia 1.8"
    Le mot-clé `base` nécessite au moins Julia 1.8.

