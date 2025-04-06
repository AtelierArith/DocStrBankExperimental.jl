```
muladd(x, y, z)
```

Birleşik çarpma-toplama: `x*y+z` hesaplar, ancak toplama ve çarpmanın birbirleriyle veya çevresindeki işlemlerle birleştirilmesine izin verir. Örneğin, bu, donanımın bunu verimli bir şekilde desteklemesi durumunda bir [`fma`](@ref) olarak uygulanabilir. Sonuç, farklı makinelerde farklı olabilir ve aynı makinede de sabit yayılımı veya diğer optimizasyonlar nedeniyle farklı olabilir. [`fma`](@ref) için bakın.

# Örnekler

```jldoctest
julia> muladd(3, 2, 1)
7

julia> 3 * 2 + 1
7
```
