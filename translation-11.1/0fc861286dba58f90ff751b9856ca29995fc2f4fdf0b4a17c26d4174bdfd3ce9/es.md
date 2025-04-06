```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

Devuelve simultáneamente el `floor` y el `ceil` de `Period` a la resolución `p`. Más eficiente que llamar a `floor` y `ceil` individualmente.
