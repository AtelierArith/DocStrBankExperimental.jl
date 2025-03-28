```
isodd(x::Number) -> Bool
```

Gibt `true` zurück, wenn `x` eine ungerade ganze Zahl ist (das heißt, eine ganze Zahl, die nicht durch 2 teilbar ist), und `false` andernfalls.

!!! compat "Julia 1.7"
    Nicht-`Integer`-Argumente erfordern Julia 1.7 oder später.


# Beispiele

```jldoctest
julia> isodd(9)
true

julia> isodd(10)
false
```
