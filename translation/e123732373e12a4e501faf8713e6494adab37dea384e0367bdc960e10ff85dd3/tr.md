```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

`A` içinde uzunluğu `n = length(A)` olan rastgele bir döngüsel permütasyon oluşturur. İsteğe bağlı `rng` argümanı, [Rastgele Sayılar](@ref) bölümünde belirtilen bir rastgele sayı üreteciyi tanımlar.

Burada "döngüsel permütasyon", tüm elemanların tek bir döngü içinde yer aldığı anlamına gelir. Eğer `A` boş değilse (`n > 0`), $(n-1)!$ olası döngüsel permütasyon vardır ve bunlar eşit olarak örneklenir. Eğer `A` boşsa, `randcycle!` onu değiştirmeden bırakır.

[`randcycle`](@ref) bu işlevin yeni bir vektör ayıran bir varyantıdır.

# Örnekler

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
