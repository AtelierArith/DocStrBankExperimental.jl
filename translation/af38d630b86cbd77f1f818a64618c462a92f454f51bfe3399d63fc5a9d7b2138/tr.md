```
MersenneTwister(seed)
MersenneTwister()
```

Bir `MersenneTwister` RNG nesnesi oluşturun. Farklı RNG nesneleri kendi tohumlarına sahip olabilir, bu da farklı rastgele sayı akışları oluşturmak için yararlı olabilir. `seed` bir tamsayı, bir dize veya `UInt32` tamsayılarının bir vektörü olabilir. Hiçbir tohum sağlanmazsa, rastgele üretilmiş bir tohum oluşturulur (sistemden entropi kullanılarak). Zaten mevcut bir `MersenneTwister` nesnesinin yeniden tohumlanması için [`seed!`](@ref) fonksiyonuna bakın.

!!! compat "Julia 1.11"
    Negatif bir tamsayı tohumunun geçmesi en az Julia 1.11 gerektirir.


# Örnekler

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
