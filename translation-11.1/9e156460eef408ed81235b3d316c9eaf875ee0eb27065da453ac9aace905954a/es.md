```
@lock l expr
```

Versión macro de `lock(f, l::AbstractLock)` pero con `expr` en lugar de la función `f`. Se expande a:

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

Esto es similar a usar [`lock`](@ref) con un bloque `do`, pero evita crear un cierre y, por lo tanto, puede mejorar el rendimiento.

!!! compat
    `@lock` se agregó en Julia 1.3 y se exportó en Julia 1.10.

