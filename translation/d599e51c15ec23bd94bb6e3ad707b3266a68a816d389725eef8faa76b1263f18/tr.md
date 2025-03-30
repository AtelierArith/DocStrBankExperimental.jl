```
takewhile(pred, iter)
```

Bir iteratör, `pred` koşulu doğru olduğu sürece `iter`'den elemanlar üretir, sonrasında her elemanı atar.

!!! compat "Julia 1.4"
    Bu fonksiyon en az Julia 1.4 gerektirir.


# Örnekler

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.takewhile(<(3),s))
2-element Vector{Int64}:
 1
 2
```
