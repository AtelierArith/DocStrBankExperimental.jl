```
isunordered(x)
```

Devuelve `true` si `x` es un valor que no se puede ordenar de acuerdo con [`<`](@ref), como `NaN` o `missing`.

Los valores que evalúan a `true` con este predicado pueden ser ordenables con respecto a otros ordenamientos como [`isless`](@ref).

!!! compat "Julia 1.7"
    Esta función requiere Julia 1.7 o posterior.

