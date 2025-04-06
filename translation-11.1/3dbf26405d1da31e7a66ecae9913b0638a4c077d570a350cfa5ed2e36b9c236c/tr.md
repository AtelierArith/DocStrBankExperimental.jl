```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

Argümanı erişilebilen tüm benzersiz nesnelerin kullandığı bellek miktarını, bayt cinsinden hesaplar.

# Anahtar Argümanlar

  * `exclude`: gezintiden hariç tutulacak nesne türlerini belirtir.
  * `chargeall`: normalde hariç tutulacak olan alanların boyutunu her zaman hesaplamak için nesne türlerini belirtir.

Ayrıca bkz. [`sizeof`](@ref).

# Örnekler

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
