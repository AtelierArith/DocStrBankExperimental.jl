```
floorceil(dt::TimeType, p::Period) -> (TimeType, TimeType)
```

Devuelve simultáneamente el `floor` y el `ceil` de un `Date` o `DateTime` a la resolución `p`. Más eficiente que llamar a `floor` y `ceil` individualmente.
