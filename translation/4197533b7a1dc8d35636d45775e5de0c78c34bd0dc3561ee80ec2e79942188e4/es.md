```
objectid(x) -> UInt
```

Obtiene un valor hash para `x` basado en la identidad del objeto.

Si `x === y` entonces `objectid(x) == objectid(y)`, y generalmente cuando `x !== y`, `objectid(x) != objectid(y)`.

Ver también [`hash`](@ref), [`IdDict`](@ref).
