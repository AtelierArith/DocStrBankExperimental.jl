```
iseven(x::Number) -> Bool
```

Gibt `true` zurück, wenn `x` eine gerade ganze Zahl ist (das heißt, eine ganze Zahl, die durch 2 teilbar ist), und `false` andernfalls.

!!! compat "Julia 1.7"
    Nicht-`Integer`-Argumente erfordern Julia 1.7 oder später.


# Beispiele

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
