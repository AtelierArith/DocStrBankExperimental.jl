```
flipsign(x, y)
```

Gibt `x` mit umgekehrtem Vorzeichen zurück, wenn `y` negativ ist. Zum Beispiel `abs(x) = flipsign(x,x)`.

# Beispiele

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
