```
shuffle([rng=default_rng(),] v::AbstractArray)
```

`v`'nin rastgele bir şekilde permütasyona uğramış bir kopyasını döndürür. İsteğe bağlı `rng` argümanı, bir rastgele sayı üreteci belirtir (bkz. [Rastgele Sayılar](@ref)). `v`'yi yerinde permütasyona uğratmak için [`shuffle!`](@ref) fonksiyonuna bakın. Rastgele permütasyona uğramış indeksler elde etmek için [`randperm`](@ref) fonksiyonuna bakın.

# Örnekler

```jldoctest
julia> shuffle(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
