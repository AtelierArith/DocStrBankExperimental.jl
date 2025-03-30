```
findmax(f, domain) -> (f(x), index)
```

Bir değer çiftini döndürür; bu değer, `f`'nin kodomaininde (çıkışları) ve `domain`'deki (girişleri) karşılık gelen değerin indeksini veya anahtarını içerir, böylece `f(x)` maksimize edilir. Birden fazla maksimum nokta varsa, ilk olanı döndürülecektir.

`domain`, [`keys`](@ref) destekleyen boş olmayan bir iterable olmalıdır. İndeksler, [`keys(domain)`](@ref) tarafından döndürülenlerle aynı türdedir.

Değerler `isless` ile karşılaştırılır.

!!! compat "Julia 1.7"
    Bu yöntem Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
