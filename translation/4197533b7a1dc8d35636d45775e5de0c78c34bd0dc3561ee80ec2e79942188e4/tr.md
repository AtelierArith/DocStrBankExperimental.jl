```
objectid(x) -> UInt
```

`x` için nesne kimliğine dayalı bir hash değeri alır.

Eğer `x === y` ise `objectid(x) == objectid(y)` olur ve genellikle `x !== y` olduğunda `objectid(x) != objectid(y)` olur.

Ayrıca bkz. [`hash`](@ref), [`IdDict`](@ref).
