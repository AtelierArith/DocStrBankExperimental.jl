```
toprev(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

Ajusta `dt` al día de la semana anterior correspondiente a `dow` con `1 = Lunes, 2 = Martes, etc`. Establecer `same=true` permite que el `dt` actual se considere como el `dow` anterior, lo que permite que no ocurra ningún ajuste.
