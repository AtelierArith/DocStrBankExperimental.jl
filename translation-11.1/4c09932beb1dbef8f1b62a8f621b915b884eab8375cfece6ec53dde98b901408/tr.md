```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

`Pair`'lerin diyagonal ve vektörlerden oluşan bir matris oluşturur. Vektör `kv.second`, `kv.first` diyagonalinde yer alacaktır. Varsayılan olarak matris kare olup boyutu `kv`'den çıkarılır, ancak `m,n`'yi ilk argümanlar olarak geçirerek dikdörtgen bir boyut `m`×`n` (gerekirse sıfırlarla doldurulmuş) belirtilebilir. Tekrar eden diyagonal indeksleri `kv.first` için, karşılık gelen vektörlerdeki `kv.second` değerleri toplanacaktır.

`diagm`, tam bir matris oluşturur; eğer hızlı aritmetik ile depolama verimli versiyonlar istiyorsanız, [`Diagonal`](@ref), [`Bidiagonal`](@ref) [`Tridiagonal`](@ref) ve [`SymTridiagonal`](@ref) bakın.

# Örnekler

```

jldoctest julia> diagm(1 => [1,2,3]) 4×4 Matrix{Int64}:  0  1  0  0  0  0  2  0  0  0  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5]) 4×4 Matrix{Int64}:  0  1  0  0  4  0  2  0  0  5  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3]) 4×4 Matrix{Int64}:  0  2  0  0  0  0  4  0  0  0  0  6  0  0  0  0 ```
