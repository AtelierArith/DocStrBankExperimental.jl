```
prevfloat(x::AbstractFloat)
```

`x` ile aynı türdeki en büyük kayan nokta sayısını `y` döndürür, böylece `y < x`. Eğer böyle bir `y` yoksa (örneğin, `x` `-Inf` veya `NaN` ise), o zaman `x`'i döndür.
