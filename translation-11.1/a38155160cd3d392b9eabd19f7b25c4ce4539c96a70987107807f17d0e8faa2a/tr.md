```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

Bir matris oluşturur ve vektörün elemanlarını köşegen elemanlar olarak kullanır. Varsayılan olarak, matris kare olup boyutu `length(v)` ile belirlenir, ancak `m,n` ilk argümanlar olarak geçilerek dikdörtgen bir boyut `m`×`n` belirtilebilir.

# Örnekler

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
