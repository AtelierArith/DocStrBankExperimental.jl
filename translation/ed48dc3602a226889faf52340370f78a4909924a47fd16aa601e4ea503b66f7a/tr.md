```
floorceil(dt::TimeType, p::Period) -> (TimeType, TimeType)
```

Bir `Date` veya `DateTime`'in `p` çözünürlüğündeki `floor` ve `ceil` değerlerini aynı anda döndürür. Hem `floor` hem de `ceil`'i ayrı ayrı çağırmaktan daha verimlidir.
