```
prevind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Durum `n == 1`

    Eğer `i` `s` içinde geçerliyse, `i` indeksinden önce başlayan karakterin başlangıç indeksini döndür. Başka bir deyişle, eğer `i` bir karakterin başlangıcıysa, önceki karakterin başlangıcını döndür; eğer `i` bir karakterin başlangıcı değilse, bir karakterin başlangıcına kadar geri sar ve o indeksi döndür. Eğer `i` `1`'e eşitse `0` döndür. Eğer `i` `ncodeunits(str)+1`'e eşitse `lastindex(str)` döndür. Aksi takdirde `BoundsError` fırlatılır.
  * Durum `n > 1`

    `n==1` için `prevind` uygulamak gibi davranır. Tek fark, eğer `n` o kadar büyükse ki `prevind` uygulamak `0`'a ulaşırsa, her kalan iterasyon döndürülen değeri `1` azaltır. Bu durumda `prevind` negatif bir değer döndürebilir.
  * Durum `n == 0`

    `i` yalnızca `str` içinde geçerli bir indeksse veya `ncodeunits(str)+1`'e eşitse döndürülür. Aksi takdirde `StringIndexError` veya `BoundsError` fırlatılır.

# Örnekler

```jldoctest
julia> prevind("α", 3)
1

julia> prevind("α", 1)
0

julia> prevind("α", 0)
HATA: BoundsError: 2-kod bir String'e [0] indeksinden erişim denemesi
[...]

julia> prevind("α", 2, 2)
0

julia> prevind("α", 2, 3)
-1
```
