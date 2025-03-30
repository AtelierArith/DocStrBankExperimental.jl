```
div(x, y, r::RoundingMode=RoundToZero)
```

Euclidean (tam sayı) bölmeden elde edilen bölüm. `x / y` hesaplar, `r` yuvarlama moduna göre bir tam sayıya yuvarlanır. Diğer bir deyişle, miktar

```
round(x / y, r)
```

herhangi bir ara yuvarlama olmadan.

!!! compat "Julia 1.4"
    `RoundingMode` alan üç argümanlı yöntem, Julia 1.4 veya daha yenisini gerektirir.


Ayrıca [`fld`](@ref) ve [`cld`](@ref) ile ilgili, bu fonksiyonun özel durumlarıdır.

!!! compat "Julia 1.9"
    `RoundFromZero` en az Julia 1.9 gerektirir.


# Örnekler:

```jldoctest
julia> div(4, 3, RoundToZero) # div(4, 3) ile eşleşir
1
julia> div(4, 3, RoundDown) # fld(4, 3) ile eşleşir
1
julia> div(4, 3, RoundUp) # cld(4, 3) ile eşleşir
2
julia> div(5, 2, RoundNearest)
2
julia> div(5, 2, RoundNearestTiesAway)
3
julia> div(-5, 2, RoundNearest)
-2
julia> div(-5, 2, RoundNearestTiesAway)
-3
julia> div(-5, 2, RoundNearestTiesUp)
-2
julia> div(4, 3, RoundFromZero)
2
julia> div(-4, 3, RoundFromZero)
-2
```
