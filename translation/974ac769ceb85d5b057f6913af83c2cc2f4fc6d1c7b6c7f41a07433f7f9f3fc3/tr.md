```
median(itr)
```

Bir koleksiyondaki tüm elemanların medyanını hesaplar. Eleman sayısı çift olduğunda, tam bir medyan elemanı yoktur, bu nedenle sonuç iki medyan elemanının ortalamasını almakla eşdeğerdir.

!!! not
    Eğer `itr` `NaN` veya [`missing`](@ref) değerleri içeriyorsa, sonuç da `NaN` veya `missing` olacaktır (`itr` hem `NaN` hem de `missing` içeriyorsa `missing` önceliklidir). `missing` girişlerini atlamak ve eksik olmayan değerlerin medyanını hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.


# Örnekler

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
