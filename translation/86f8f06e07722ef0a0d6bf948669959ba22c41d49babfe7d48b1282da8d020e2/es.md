```
argmax(f, domain)
```

Devuelve un valor `x` de `domain` para el cual `f(x)` está maximizado. Si hay múltiples valores máximos para `f(x)`, se encontrará el primero.

`domain` debe ser un iterable no vacío.

Los valores se comparan con `isless`.

!!! compat "Julia 1.7"
    Este método requiere Julia 1.7 o posterior.


Véase también [`argmin`](@ref), [`findmax`](@ref).

# Ejemplos

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
