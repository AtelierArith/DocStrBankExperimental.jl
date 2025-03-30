```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

`Pair`'lerden ve diyagonalardan oluşan seyrek bir diyagonal matris oluşturur. Her bir vektör `kv.second`, `kv.first` diyagonalında yer alacaktır. Varsayılan olarak, matris kare olup boyutu `kv`'den çıkarılır, ancak `m,n` ilk argümanlar olarak geçilerek dikdörtgen bir boyut `m`×`n` (gerekirse sıfırlarla doldurulmuş) belirtilebilir.

# Örnekler

```

jldoctest julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1]) 5×5 SparseMatrixCSC{Int64, Int64} with 8 stored entries:  ⋅  4  ⋅  ⋅  ⋅  1  ⋅  3  ⋅  ⋅  ⋅  2  ⋅  2  ⋅  ⋅  ⋅  3  ⋅  1  ⋅  ⋅  ⋅  4  ⋅ ```
