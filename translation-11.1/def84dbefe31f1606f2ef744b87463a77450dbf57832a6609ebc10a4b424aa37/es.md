```
cbrt(x::Real)
```

Devuelve la raíz cúbica de `x`, es decir, $x^{1/3}$. Se aceptan valores negativos (devolviendo la raíz real negativa cuando $x < 0$).

El operador prefijo `∛` es equivalente a `cbrt`.

# Ejemplos

```jldoctest
julia> cbrt(big(27))
3.0

julia> cbrt(big(-27))
-3.0
```
