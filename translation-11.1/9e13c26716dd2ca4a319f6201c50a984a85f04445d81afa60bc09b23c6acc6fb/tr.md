```
thisind(s::AbstractString, i::Integer) -> Int
```

Eğer `i`, `s` içinde sınırlar içindeyse, `i`'nin parçası olduğu karakterin kodlama kod biriminin başlangıç indeksini döndür. Başka bir deyişle, eğer `i` bir karakterin başlangıcıysa, `i`'yi döndür; eğer `i` bir karakterin başlangıcı değilse, bir karakterin başlangıcına kadar geri sar ve o indeksi döndür. Eğer `i`, 0 veya `ncodeunits(s)+1`'e eşitse, `i`'yi döndür. Diğer tüm durumlarda `BoundsError` fırlat.

# Örnekler

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
HATA: BoundsError: 2-kod birimlik String'e [4] indeksinde erişim denemesi
[...]

julia> thisind("α", -1)
HATA: BoundsError: 2-kod birimlik String'e [-1] indeksinde erişim denemesi
[...]
```
