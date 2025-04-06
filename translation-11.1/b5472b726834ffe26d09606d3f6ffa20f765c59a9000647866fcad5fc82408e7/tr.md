```
var(itr; corrected::Bool=true, mean=nothing[, dims])
```

`itr` koleksiyonunun örnek varyansını hesaplayın.

Algoritma, `itr`'nin her bir girişinin aynı bilinmeyen dağılımdan çekilmiş bir örnek olduğu varsayımı altında, üretken dağılımın varyansının bir tahmincisini döndürür ve örneklerin birbirleriyle ilişkili olmadığı varsayılır. Diziler için bu hesaplama, `sum((itr .- mean(itr)).^2) / (length(itr) - 1)` hesaplamasıyla eşdeğerdir. Eğer `corrected` `true` ise, toplam `n-1` ile ölçeklendirilir; `corrected` `false` ise toplam `n` ile ölçeklendirilir; burada `n`, `itr`'deki eleman sayısını temsil eder.

Eğer `itr` bir `AbstractArray` ise, varyansı boyutlar üzerinde hesaplamak için `dims` sağlanabilir.

Önceden hesaplanmış bir `mean` sağlanabilir. `dims` belirtildiğinde, `mean`, `mean(itr, dims=dims)` ile aynı şekle sahip bir dizi olmalıdır (ekstra son tekil boyutlara izin verilir).

!!! not
    Eğer dizi `NaN` veya [`missing`](@ref) değerleri içeriyorsa, sonuç da `NaN` veya `missing` olur (`dizi her ikisini de içeriyorsa`missing`önceliklidir).`missing`girişlerini atlamak ve eksik olmayan değerlerin varyansını hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.

