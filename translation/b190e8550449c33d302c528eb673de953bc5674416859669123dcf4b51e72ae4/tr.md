```
Sıfırdan Yuvarlama
```

Sıfırdan uzaklaştırır.

!!! uyum "Julia 1.9"
    `RoundFromZero` en az Julia 1.9 gerektirir. Önceki sürümler yalnızca `BigFloat`'lar için `RoundFromZero`'yu destekler.


# Örnekler

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
