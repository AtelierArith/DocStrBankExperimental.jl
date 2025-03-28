```
Some{T}
```

Un tipo de envoltura utilizado en `Union{Some{T}, Nothing}` para distinguir entre la ausencia de un valor ([`nothing`](@ref)) y la presencia de un valor `nothing` (es decir, `Some(nothing)`).

Utiliza [`something`](@ref) para acceder al valor envuelto por un objeto `Some`.
