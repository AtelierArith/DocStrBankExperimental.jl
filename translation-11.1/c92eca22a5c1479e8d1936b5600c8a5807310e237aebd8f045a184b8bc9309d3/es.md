```
tonext(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

Ajusta `dt` al siguiente día de la semana correspondiente a `dow` con `1 = Lunes, 2 = Martes, etc`. Establecer `same=true` permite que el `dt` actual se considere como el siguiente `dow`, lo que permite que no se realice ningún ajuste.
