```
tonext(func::Function, dt::TimeType; step=Day(1), limit=10000, same=false) -> TimeType
```

Ajuste `dt` en itérant au maximum `limit` itérations par des incréments de `step` jusqu'à ce que `func` retourne `true`. `func` doit prendre un seul argument de type `TimeType` et retourner un [`Bool`](@ref). `same` permet de considérer `dt` comme satisfaisant `func`.
