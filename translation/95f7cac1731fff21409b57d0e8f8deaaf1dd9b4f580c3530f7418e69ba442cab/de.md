```
copysign(x, y) -> z
```

Gibt `z` zurück, das die Größe von `x` und das gleiche Vorzeichen wie `y` hat.

# Beispiele

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
