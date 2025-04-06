```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

Aynı anda `Period`'ün `p` çözünürlüğündeki `floor` ve `ceil` değerlerini döndürür. Hem `floor` hem de `ceil`'i ayrı ayrı çağırmaktan daha verimlidir.
