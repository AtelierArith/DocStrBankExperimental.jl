```
toprev(func::Function, dt::TimeType; step=Day(-1), limit=10000, same=false) -> TimeType
```

Passt `dt` an, indem es höchstens `limit` Iterationen mit `step` Inkrementen durchläuft, bis `func` `true` zurückgibt. `func` muss ein einzelnes `TimeType` Argument annehmen und einen [`Bool`](@ref) zurückgeben. `same` erlaubt es, `dt` bei der Erfüllung von `func` zu berücksichtigen.
