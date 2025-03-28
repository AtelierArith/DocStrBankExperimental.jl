```
mod2pi(x)
```

Módulo después de la división por `2π`, devolviendo en el rango $[0,2π)$.

Esta función calcula una representación de punto flotante del módulo después de la división por `2π` numéricamente exacto, y por lo tanto no es exactamente lo mismo que `mod(x,2π)`, que calcularía el módulo de `x` en relación con la división por el número de punto flotante `2π`.

!!! note
    Dependiendo del formato del valor de entrada, el valor representable más cercano a 2π puede ser menor que 2π. Por ejemplo, la expresión `mod2pi(2π)` no devolverá `0`, porque el valor intermedio de `2*π` es un `Float64` y `2*Float64(π) < 2*big(π)`. Consulte [`rem2pi`](@ref) para un control más refinado de este comportamiento.


# Ejemplos

```jldoctest
julia> mod2pi(9*pi/4)
0.7853981633974481
```
