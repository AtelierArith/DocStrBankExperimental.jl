```
varm(itr, mean; dims, corrected::Bool=true)
```

Koleksiyon `itr`'nin örnek varyansını, bilinen ortalama(lar) `mean` ile hesaplar.

Algoritma, `itr`'nin her bir girişinin aynı bilinmeyen dağılımdan çekilmiş bir örnek olduğu varsayımı altında, üretken dağılımın varyansının bir tahmincisini döndürür ve örneklerin birbirleriyle ilişkili olmadığı varsayılır. Diziler için bu hesaplama, `sum((itr .- mean(itr)).^2) / (length(itr) - 1)` hesaplamasına eşdeğerdir. Eğer `corrected` `true` ise, toplam `n-1` ile ölçeklendirilir; `corrected` `false` ise toplam `n` ile ölçeklendirilir, burada `n` `itr`'deki eleman sayısını ifade eder.

Eğer `itr` bir `AbstractArray` ise, varyansı boyutlar üzerinde hesaplamak için `dims` sağlanabilir. Bu durumda, `mean` `mean(itr, dims=dims)` ile aynı şekle sahip bir dizi olmalıdır (ekstra son tekil boyutlara izin verilir).

!!! note
    Eğer dizi `NaN` veya [`missing`](@ref) değerleri içeriyorsa, sonuç da `NaN` veya `missing` olur (`missing` her ikisi de varsa önceliklidir). `missing` girişlerini atlamak ve eksik olmayan değerlerin varyansını hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.

