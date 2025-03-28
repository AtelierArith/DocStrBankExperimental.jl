```
RoundFromZero
```

Redondea alejándose de cero.

!!! compat "Julia 1.9"
    `RoundFromZero` requiere al menos Julia 1.9. Las versiones anteriores solo admiten `RoundFromZero` para `BigFloat`s.


# Ejemplos

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
