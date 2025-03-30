```
stdm(itr, mean; corrected::Bool=true[, dims])
```

Koleksiyon `itr`'nin örnek standart sapmasını, bilinen ortalama(lar) `mean` ile hesaplar.

Algoritma, `itr`'nin her bir girişinin aynı bilinmeyen dağılımdan çekilmiş bir örnek olduğu varsayımı altında, üretken dağılımın standart sapmasının bir tahmincisini döndürür ve örneklerin birbirleriyle ilişkili olmadığını varsayar. Diziler için bu hesaplama, `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))` hesaplamasıyla eşdeğerdir. Eğer `corrected` `true` ise, toplam `n-1` ile ölçeklendirilir; `corrected` `false` ise toplam `n` ile ölçeklendirilir, burada `n` `itr`'deki eleman sayısını ifade eder.

Eğer `itr` bir `AbstractArray` ise, boyutlar üzerinde standart sapmayı hesaplamak için `dims` sağlanabilir. Bu durumda, `mean` `mean(itr, dims=dims)` ile aynı şekle sahip bir dizi olmalıdır (ekstra son tekil boyutlara izin verilir).

!!! not
    Eğer dizi `NaN` veya [`missing`](@ref) değerleri içeriyorsa, sonuç da `NaN` veya `missing` olacaktır (`missing` her ikisi de varsa önceliklidir). `missing` girişlerini atlamak ve eksik olmayan değerlerin standart sapmasını hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.

