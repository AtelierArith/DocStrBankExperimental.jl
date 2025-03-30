```
nextfloat(x::AbstractFloat)
```

`x` ile aynı türdeki en küçük kayan nokta sayısını `y` döndürür, böylece `x < y`. Eğer böyle bir `y` yoksa (örneğin, `x` `Inf` veya `NaN` ise), o zaman `x` döndürülür.

Ayrıca bakınız: [`prevfloat`](@ref), [`eps`](@ref), [`issubnormal`](@ref).
