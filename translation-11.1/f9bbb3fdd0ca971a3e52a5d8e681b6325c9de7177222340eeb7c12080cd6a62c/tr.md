```
findmin(f, domain) -> (f(x), index)
```

Bir değer çiftini döndürür; bu değer, `f`'nin kodomaininde (çıkışları) ve `f`'ye karşılık gelen değerin `domain`'deki (girişleri) indeks veya anahtarıdır, böylece `f(x)` en aza indirilir. Birden fazla minimal nokta varsa, ilk olanı döndürülecektir.

`domain` boş olmayan bir iterable olmalıdır.

İndeksler, [`keys(domain)`](@ref) ve [`pairs(domain)`](@ref) tarafından döndürülenlerle aynı türdedir.

`NaN`, `missing` hariç tüm diğer değerlerden daha küçük olarak kabul edilir.

!!! compat "Julia 1.7"
    Bu yöntem Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
