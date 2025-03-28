```
objectid(x) -> UInt
```

Erhalte einen Hash-Wert für `x`, basierend auf der Objektidentität.

Wenn `x === y`, dann ist `objectid(x) == objectid(y)`, und normalerweise, wenn `x !== y`, ist `objectid(x) != objectid(y)`.

Siehe auch [`hash`](@ref), [`IdDict`](@ref).
