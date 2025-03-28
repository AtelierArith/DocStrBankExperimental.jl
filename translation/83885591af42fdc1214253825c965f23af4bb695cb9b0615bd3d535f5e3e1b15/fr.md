```
issubnormal(f) -> Bool
```

Testez si un nombre à virgule flottante est subnormal.

Un nombre à virgule flottante IEEE est [subnormal](https://en.wikipedia.org/wiki/Subnormal_number) lorsque ses bits d'exposant sont zéro et que son significand n'est pas zéro.

# Exemples

```jldoctest
julia> floatmin(Float32)
1.1754944f-38

julia> issubnormal(1.0f-37)
false

julia> issubnormal(1.0f-38)
true
```
