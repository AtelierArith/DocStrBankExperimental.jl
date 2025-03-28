```
tonext(func::Function, dt::TimeType; step=Day(1), limit=10000, same=false) -> TimeType
```

Ajusta `dt` iterando como máximo `limit` iteraciones por incrementos de `step` hasta que `func` devuelva `true`. `func` debe tomar un único argumento de tipo `TimeType` y devolver un [`Bool`](@ref). `same` permite que `dt` se considere al satisfacer `func`.
