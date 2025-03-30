```
popat!(a::Vector, i::Integer, [default])
```

Verilen `i`'deki öğeyi kaldırır ve onu döndürür. Sonraki öğeler, oluşan boşluğu doldurmak için kaydırılır. `i`, `a` için geçerli bir indeks değilse, `default`'u döndürür veya `default` belirtilmemişse bir hata fırlatır.

Ayrıca bakınız: [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    Bu fonksiyon Julia 1.5 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
3-element Vector{Int64}:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
HATA: BoundsError: 3-element Vector{Int64} üzerinde [4] indeksine erişim denemesi
[...]
```
