```
modf(x)
```

Bir sayının kesirli ve tam kısımlarını içeren `(fpart, ipart)` demetini döndürür. Her iki kısım da argümanın aynı işaretine sahiptir.

# Örnekler

```jldoctest
julia> modf(3.5)
(0.5, 3.0)

julia> modf(-3.5)
(-0.5, -3.0)
```
