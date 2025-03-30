```
quantile(itr, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Bir koleksiyon `itr` için belirtilen olasılık veya olasılıkların vektörü veya demeti `p` üzerinde [0,1] aralığında kuantil(ler) hesaplayın. Anahtar kelime argümanı `sorted`, `itr`'nin sıralı olduğu varsayımında bulunulup bulunulamayacağını belirtir.

Örnek kuantiller, `Q(p) = (1-γ)*x[j] + γ*x[j+1]` ile tanımlanır; burada `x[j]`, `itr`'nin j-inci sıralama istatistiğidir, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` ve `γ = n*p + m - j`.

Varsayılan olarak (`alpha = beta = 1`), kuantiller, `((k-1)/(n-1), x[k])` noktaları arasında lineer interpolasyon yoluyla hesaplanır; burada `k = 1:n` ve `n = length(itr)`. Bu, Hyndman ve Fan (1996)'nın Tanım 7'sine karşılık gelir ve R ve NumPy varsayılanı ile aynıdır.

Anahtar kelime argümanları `alpha` ve `beta`, Hyndman ve Fan'daki aynı parametrelere karşılık gelir; bunları farklı değerlere ayarlamak, bu makalede tanımlanan 4-9 yöntemleri ile kuantillerin hesaplanmasına olanak tanır:

  * Tanım 4: `alpha=0`, `beta=1`
  * Tanım 5: `alpha=0.5`, `beta=0.5` (MATLAB varsayılanı)
  * Tanım 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, Python varsayılanı, Stata `altdef`)
  * Tanım 7: `alpha=1`, `beta=1` (Julia, R ve NumPy varsayılanı, Excel `PERCENTILE` ve `PERCENTILE.INC`, Python `'inclusive'`)
  * Tanım 8: `alpha=1/3`, `beta=1/3`
  * Tanım 9: `alpha=3/8`, `beta=3/8`

!!! not
    Eğer `v` `NaN` veya [`missing`](@ref) değerleri içeriyorsa bir `ArgumentError` fırlatılır. `missing` girişlerini atlamak ve eksik olmayan değerlerin kuantillerini hesaplamak için [`skipmissing`](@ref) fonksiyonunu kullanın.


# Kaynaklar

  * Hyndman, R.J ve Fan, Y. (1996) "Statistik Paketlerinde Örnek Kuantilleri", *The American Statistician*, Cilt. 50, No. 4, ss. 361-365
  * [Wikipedia'da Kuantil](https://en.m.wikipedia.org/wiki/Quantile) farklı kuantil tanımlarını detaylandırmaktadır

# Örnekler

```jldoctest
julia> using Statistics

julia> quantile(0:20, 0.5)
10.0

julia> quantile(0:20, [0.1, 0.5, 0.9])
3-element Vector{Float64}:
  2.0
 10.0
 18.000000000000004

julia> quantile(skipmissing([1, 10, missing]), 0.5)
5.5
```
