```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

1 ölçekli üstel dağılıma göre `T` türünde rastgele bir sayı üretir. İsteğe bağlı olarak, bu türde rastgele sayıların bir dizisini de üretebilir. `Base` modülü şu türler için bir uygulama sağlar: [`Float16`](@ref), [`Float32`](@ref) ve [`Float64`](@ref) (varsayılan).

# Örnekler

```jldoctest
julia> rng = Xoshiro(123);

julia> randexp(rng, Float32)
1.1757717f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.37766  0.456653  0.236418
 3.40007  0.229917  0.0684921
 0.48096  0.577481  0.71835
```
