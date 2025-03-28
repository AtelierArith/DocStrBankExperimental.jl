```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

Retourne simultanément le `floor` et le `ceil` de `Period` à la résolution `p`. Plus efficace que d'appeler `floor` et `ceil` individuellement.
