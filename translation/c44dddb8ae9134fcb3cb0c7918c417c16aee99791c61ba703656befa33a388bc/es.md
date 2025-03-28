```
Base.checked_length(r)
```

Calcula `length(r)`, pero puede verificar errores de desbordamiento donde sea aplicable cuando el resultado no cabe en `Union{Integer(eltype(r)),Int}`.
