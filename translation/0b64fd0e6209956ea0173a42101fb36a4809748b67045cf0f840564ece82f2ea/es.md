```
nextfloat(x::AbstractFloat)
```

Devuelve el número de punto flotante más pequeño `y` del mismo tipo que `x` tal que `x < y`. Si no existe tal `y` (por ejemplo, si `x` es `Inf` o `NaN`), entonces devuelve `x`.

Véase también: [`prevfloat`](@ref), [`eps`](@ref), [`issubnormal`](@ref).
