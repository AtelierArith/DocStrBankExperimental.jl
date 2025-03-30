```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

`A` içinde `length(A)` uzunluğunda rastgele bir permütasyon oluşturur. İsteğe bağlı `rng` argümanı, bir rastgele sayı üreteci belirtir (bkz. [Rastgele Sayılar](@ref)). Rastgele bir vektörü permüte etmek için [`shuffle`](@ref) veya [`shuffle!`](@ref) fonksiyonlarına bakın.

# Örnekler

```jldoctest
julia> randperm!(Xoshiro(123), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 1
 4
 2
 3
```
