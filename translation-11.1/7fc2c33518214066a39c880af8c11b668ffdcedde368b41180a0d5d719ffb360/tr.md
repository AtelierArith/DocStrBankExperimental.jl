```
mean(itr)
```

Bir koleksiyondaki tüm elemanların ortalamasını hesaplayın.

!!! not
    Eğer `itr` `NaN` veya [`missing`](@ref) değerleri içeriyorsa, sonuç da `NaN` veya `missing` olacaktır (`missing`, dizi her ikisini de içeriyorsa önceliklidir). `missing` girişlerini atlamak ve eksik olmayan değerlerin ortalamasını hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.


# Örnekler

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
