```
!=(x, y)
≠(x,y)
```

Operador de comparación de desigualdad. Siempre da la respuesta opuesta a [`==`](@ref).

# Implementación

Los nuevos tipos generalmente no deben implementar esto y deben confiar en la definición de respaldo `!=(x,y) = !(x==y)` en su lugar.

# Ejemplos

```jldoctest
julia> 3 != 2
true

julia> "foo" ≠ "foo"
false
```
