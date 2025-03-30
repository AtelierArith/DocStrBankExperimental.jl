```
Iterators.map(f, iterators...)
```

Tembel bir eşleme oluşturur. Bu, `(f(args...) for args in zip(iterators...))` yazmanın başka bir sözdizimidir.

!!! uyumluluk "Julia 1.6"
    Bu fonksiyon en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```
