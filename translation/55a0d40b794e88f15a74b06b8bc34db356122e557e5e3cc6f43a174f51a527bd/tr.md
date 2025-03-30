```
randcycle([rng=default_rng(),] n::Integer)
```

`n` uzunluğunda rastgele bir döngüsel permütasyon oluşturur. İsteğe bağlı `rng` argümanı, [Rastgele Sayılar](@ref) bölümünde belirtilen bir rastgele sayı üreteciyi tanımlar. Sonucun eleman tipi, `n`'nin tipiyle aynıdır.

Burada "döngüsel permütasyon", tüm elemanların tek bir döngü içinde yer aldığı anlamına gelir. Eğer `n > 0` ise, $(n-1)!$ olası döngüsel permütasyon vardır ve bunlar eşit olarak örneklenir. Eğer `n == 0` ise, `randcycle` boş bir vektör döner.

[`randcycle!`](@ref) bu işlevin yerinde bir varyantıdır.

!!! uyumluluk "Julia 1.1"
    Julia 1.1 ve üzeri sürümlerde, `randcycle` `eltype(v) == typeof(n)` olan bir vektör `v` dönerken, Julia 1.0'da `eltype(v) == Int`'dir.


# Örnekler

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
