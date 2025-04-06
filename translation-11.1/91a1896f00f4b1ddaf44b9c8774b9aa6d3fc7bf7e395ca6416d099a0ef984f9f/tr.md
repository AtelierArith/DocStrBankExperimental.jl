```
@views ifade
```

Verilen ifadede (bu bir `begin`/`end` bloğu, döngü, fonksiyon vb. olabilir) her dizi dilimleme işlemini bir görünüm döndürecek şekilde dönüştürün. Skalar indeksler, dizi olmayan türler ve açık [`getindex`](@ref) çağrıları (dizi[...] yerine) etkilenmez.

Benzer şekilde, `@views` dize dilimlerini [`SubString`](@ref) görünümlerine dönüştürür.

!!! not
    `@views` makrosu yalnızca verilen `ifade` içinde açıkça görünen `dizi[...]` ifadelerini etkiler, o kod tarafından çağrılan fonksiyonlarda gerçekleşen dizi dilimleme işlemlerini etkilemez.


!!! uyumluluk "Julia 1.5"
    Bir indeksleme ifadesinde ilk indeksi belirtmek için `begin` kullanımı Julia 1.4'te uygulanmıştır, ancak yalnızca Julia 1.5'ten itibaren `@views` tarafından desteklenmiştir.


# Örnekler

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b bir görünüm, kopya değil
           b .= row      # her elemanı satır indeksine atayın
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
