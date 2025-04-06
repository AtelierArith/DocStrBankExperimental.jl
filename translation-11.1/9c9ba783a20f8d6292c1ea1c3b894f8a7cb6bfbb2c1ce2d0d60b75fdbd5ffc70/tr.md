```
quantile!([q::AbstractArray, ] v::AbstractVector, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

Bir vektör `v` için belirtilen olasılık veya olasılıkların vektörü veya demeti `p` üzerinde [0,1] aralığında kuantil(ler) hesaplayın. Eğer `p` bir vektör ise, isteğe bağlı bir çıktı dizisi `q` de belirtilebilir. (Sağlanmazsa, yeni bir çıktı dizisi oluşturulur.) Anahtar kelime argümanı `sorted`, `v`'nin sıralı olduğu varsayımını belirtir; eğer `false` (varsayılan), o zaman `v`'nin elemanları yerinde kısmen sıralanacaktır.

Örnek kuantiller `Q(p) = (1-γ)*x[j] + γ*x[j+1]` ile tanımlanır; burada `x[j]`, `v`'nin j-inci sıralama istatistiğidir, `j = floor(n*p + m)`, `m = alpha + p*(1 - alpha - beta)` ve `γ = n*p + m - j`.

Varsayılan olarak (`alpha = beta = 1`), kuantiller, `((k-1)/(n-1), x[k])` noktaları arasında lineer interpolasyon ile hesaplanır; burada `k = 1:n` ve `n = length(v)`. Bu, Hyndman ve Fan (1996) tanım 7'sine karşılık gelir ve R ve NumPy varsayılanı ile aynıdır.

Anahtar kelime argümanları `alpha` ve `beta`, Hyndman ve Fan'daki aynı parametrelere karşılık gelir; bunları farklı değerlere ayarlamak, bu makalede tanımlanan 4-9 yöntemleri ile kuantillerin hesaplanmasına olanak tanır:

  * Tanım 4: `alpha=0`, `beta=1`
  * Tanım 5: `alpha=0.5`, `beta=0.5` (MATLAB varsayılanı)
  * Tanım 6: `alpha=0`, `beta=0` (Excel `PERCENTILE.EXC`, Python varsayılanı, Stata `altdef`)
  * Tanım 7: `alpha=1`, `beta=1` (Julia, R ve NumPy varsayılanı, Excel `PERCENTILE` ve `PERCENTILE.INC`, Python `'inclusive'`)
  * Tanım 8: `alpha=1/3`, `beta=1/3`
  * Tanım 9: `alpha=3/8`, `beta=3/8`

!!! not
    Eğer `v` `NaN` veya [`missing`](@ref) değerleri içeriyorsa bir `ArgumentError` fırlatılır.


# Kaynaklar

  * Hyndman, R.J ve Fan, Y. (1996) "Sample Quantiles in Statistical Packages", *The American Statistician*, Cilt. 50, No. 4, ss. 361-365
  * [Wikipedia'da Kuantil](https://en.m.wikipedia.org/wiki/Quantile) farklı kuantil tanımlarını detaylandırmaktadır

# Örnekler

```jldoctest
julia> using Statistics

julia> x = [3, 2, 1];

julia> quantile!(x, 0.5)
2.0

julia> x
3-element Vector{Int64}:
 1
 2
 3

julia> y = zeros(3);

julia> quantile!(y, x, [0.1, 0.5, 0.9]) === y
true

julia> y
3-element Vector{Float64}:
 1.2000000000000002
 2.0
 2.8000000000000003
```
