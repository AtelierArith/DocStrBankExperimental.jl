```
objectid(x) -> UInt
```

Obtenez une valeur de hachage pour `x` basée sur l'identité de l'objet.

Si `x === y` alors `objectid(x) == objectid(y)`, et généralement lorsque `x !== y`, `objectid(x) != objectid(y)`.

Voir aussi [`hash`](@ref), [`IdDict`](@ref).
