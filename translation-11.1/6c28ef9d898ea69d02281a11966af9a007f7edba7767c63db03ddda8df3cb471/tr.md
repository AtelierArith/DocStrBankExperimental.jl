```
randperm([rng=default_rng(),] n::Integer)
```

`n` uzunluğunda rastgele bir permütasyon oluşturur. İsteğe bağlı `rng` argümanı bir rastgele sayı üreteci belirtir (bkz. [Rastgele Sayılar](@ref)). Sonucun eleman tipi, `n`'nin tipiyle aynıdır.

Rastgele bir vektörü permüte etmek için [`shuffle`](@ref) veya [`shuffle!`](@ref) fonksiyonlarına bakın.

!!! uyumluluk "Julia 1.1"
    Julia 1.1'de `randperm`, `eltype(v) == typeof(n)` olan bir vektör `v` dönerken, Julia 1.0'da `eltype(v) == Int` döner.


# Örnekler

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
