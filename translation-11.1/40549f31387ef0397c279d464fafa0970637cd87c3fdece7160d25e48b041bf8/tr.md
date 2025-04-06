```
ascii(s::AbstractString)
```

Bir dizeyi `String` türüne dönüştürür ve yalnızca ASCII verileri içerdiğini kontrol eder, aksi takdirde ilk non-ASCII baytının konumunu belirten bir `ArgumentError` fırlatır.

Ayrıca, non-ASCII karakterleri filtrelemek veya değiştirmek için [`isascii`](@ref) predikatını da inceleyin.

# Örnekler

```jldoctest
julia> ascii("abcdeγfgh")
HATA: ArgumentError: geçersiz ASCII "abcdeγfgh" dizisinde 6. indekste
Yığın izi:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
