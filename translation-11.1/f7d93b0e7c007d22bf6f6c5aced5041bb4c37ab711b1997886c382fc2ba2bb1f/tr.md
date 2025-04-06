```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Durum `n == 1`

    Eğer `i` `s` içinde geçerliyse, `i` indeksinden sonra başlayan karakterin başlangıç indeksini döndür. Başka bir deyişle, eğer `i` bir karakterin başlangıcıysa, bir sonraki karakterin başlangıcını döndür; eğer `i` bir karakterin başlangıcı değilse, bir karakterin başlangıcına kadar ilerle ve o indeksi döndür. Eğer `i` `0`'a eşitse `1` döndür. Eğer `i` geçerli bir indeksse ama `lastindex(str)`'ten büyük veya eşitse `ncodeunits(str)+1` döndür. Aksi takdirde `BoundsError` fırlatılır.
  * Durum `n > 1`

    `n==1` için `nextind` uygulamak gibi davranır. Tek fark, eğer `n` o kadar büyükse ki `nextind` uygulamak `ncodeunits(str)+1`'e ulaşırsa, kalan her iterasyon döndürülen değeri `1` artırır. Bu, bu durumda `nextind`'in `ncodeunits(str)+1`'den büyük bir değer döndürebileceği anlamına gelir.
  * Durum `n == 0`

    `i` yalnızca `s` içinde geçerli bir indeksse veya `0`'a eşitse döndürülür. Aksi takdirde `StringIndexError` veya `BoundsError` fırlatılır.

# Örnekler

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
HATA: BoundsError: [3] indeksinde 2-kod bir String'e erişim denemesi
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
