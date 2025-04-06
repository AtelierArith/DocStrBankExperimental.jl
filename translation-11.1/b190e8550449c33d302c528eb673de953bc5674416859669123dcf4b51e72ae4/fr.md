```
RoundFromZero
```

Arrondit loin de zéro.

!!! compat "Julia 1.9"
    `RoundFromZero` nécessite au moins Julia 1.9. Les versions antérieures prennent en charge `RoundFromZero` uniquement pour les `BigFloat`s.


# Exemples

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
