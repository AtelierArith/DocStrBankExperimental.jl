```
filter(f, a)
```

`f`'nin `false` olduğu elemanları çıkararak `a` koleksiyonunun bir kopyasını döndürür. `f` fonksiyonuna bir argüman geçirilir.

!!! compat "Julia 1.4"
    `a`'nın bir demet olarak desteklenmesi en az Julia 1.4 gerektirir.


Ayrıca bakınız: [`filter!`](@ref), [`Iterators.filter`](@ref).

# Örnekler

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
