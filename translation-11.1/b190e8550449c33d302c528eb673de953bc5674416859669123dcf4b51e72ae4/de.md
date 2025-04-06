```
RoundFromZero
```

Rundet von null weg.

!!! compat "Julia 1.9"
    `RoundFromZero` erfordert mindestens Julia 1.9. Frühere Versionen unterstützen `RoundFromZero` nur für `BigFloat`s.


# Beispiele

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
