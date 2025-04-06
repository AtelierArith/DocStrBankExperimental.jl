```
widen(x)
```

Eğer `x` bir tür ise, aritmetik işlemlerin `+` ve `-` herhangi bir `x` türünün tutabileceği değer kombinasyonu için taşma yapmayacağı veya hassasiyet kaybetmeyeceği şekilde tanımlanmış "daha büyük" bir tür döndürür.

128 bitten daha az sabit boyutlu tam sayı türleri için, `widen` iki katı bit sayısına sahip bir tür döndürecektir.

Eğer `x` bir değer ise, `widen(typeof(x))`'e dönüştürülür.

# Örnekler

```jldoctest
julia> widen(Int32)
Int64

julia> widen(1.5f0)
1.5
```
