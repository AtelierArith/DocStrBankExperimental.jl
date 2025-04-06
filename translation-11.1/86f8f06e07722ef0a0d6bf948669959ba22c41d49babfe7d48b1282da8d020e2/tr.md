```
argmax(f, domain)
```

`f(x)`'in maksimize edildiği `domain`'den bir değer `x` döndürür. Eğer `f(x)` için birden fazla maksimum değer varsa, ilki bulunacaktır.

`domain` boş olmayan bir iterable olmalıdır.

Değerler `isless` ile karşılaştırılır.

!!! uyumluluk "Julia 1.7"
    Bu yöntem Julia 1.7 veya daha yenisini gerektirir.


Ayrıca bkz. [`argmin`](@ref), [`findmax`](@ref).

# Örnekler

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
