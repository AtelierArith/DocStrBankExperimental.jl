```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

Bir seyrek matris oluşturur ve vektörün elemanlarını köşegen elemanları olarak kullanır. Varsayılan olarak (verilen `m` ve `n` yoksa), matris kare olup boyutu `length(v)` ile belirlenir, ancak `m` ve `n` ilk argümanlar olarak geçilerek dikdörtgen bir boyut `m`×`n` belirtilebilir.

!!! compat "Julia 1.6"
    Bu fonksiyonlar en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} with 2 stored entries:
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
