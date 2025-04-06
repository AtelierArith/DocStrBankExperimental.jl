```
Iterators.accumulate(f, itr; [init])
```

İki argümanlı `f` fonksiyonu ve bir iterator `itr` verildiğinde, `f`'yi önceki değere ve `itr`'nin bir sonraki elemanına ardışık olarak uygulayan yeni bir iterator döndürür.

Bu, etkili bir şekilde [`Base.accumulate`](@ref) fonksiyonunun tembel bir versiyonudur.

!!! compat "Julia 1.5"
    Anahtar argümanı `init`, Julia 1.5'te eklenmiştir.


# Örnekler

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
