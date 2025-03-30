```
merge(a::NamedTuple, bs::NamedTuple...)
```

İki veya daha fazla mevcut named tuple'ı soldan sağa doğru birleştirerek yeni bir named tuple oluşturur. Birleştirme, named tuple çiftleri arasında soldan sağa doğru gerçekleşir ve bu nedenle en soldaki ve en sağdaki named tuple'larda bulunan alanların sırası, en soldaki named tuple'da bulundukları konumu alır. Ancak, değerler, o alanı içeren en sağdaki named tuple'daki eşleşen alanlardan alınır. Bir çiftin yalnızca en sağdaki named tuple'ında bulunan alanlar sona eklenir. Sadece bir tane named tuple sağlandığında bir yedekleme uygulanır; imzası `merge(a::NamedTuple)` şeklindedir.

!!! compat "Julia 1.1"
    3 veya daha fazla `NamedTuple` birleştirmek en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> merge((a=1, b=2, c=3), (b=4, d=5))
(a = 1, b = 4, c = 3, d = 5)
```

```jldoctest
julia> merge((a=1, b=2), (b=3, c=(d=1,)), (c=(d=2,),))
(a = 1, b = 3, c = (d = 2,))
```
