```
@inbounds(blk)
```

Elimina la verificación de límites de matriz dentro de las expresiones.

En el ejemplo a continuación, se omite la verificación de rango para referenciar el elemento `i` de la matriz `A` para mejorar el rendimiento.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! warning
    Usar `@inbounds` puede devolver resultados incorrectos/caídas/corrupción para índices fuera de límites. El usuario es responsable de verificarlo manualmente. Solo use `@inbounds` cuando esté seguro, según la información disponible localmente, de que todos los accesos están dentro de los límites. En particular, usar `1:length(A)` en lugar de `eachindex(A)` en una función como la anterior *no* está seguro dentro de los límites porque el primer índice de `A` puede no ser `1` para todos los tipos definidos por el usuario que son subtipos de `AbstractArray`.

