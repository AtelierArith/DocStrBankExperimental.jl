```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++ hızlı bir sahte rastgele sayı üreteci olup, David Blackman ve Sebastiano Vigna tarafından "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021'de tanımlanmıştır. Referans uygulaması https://prng.di.unimi.it adresinde mevcuttur.

Yüksek hızın yanı sıra, Xoshiro'nun küçük bir bellek ayak izi vardır, bu da onu birçok farklı rastgele durumun uzun süre tutulması gereken uygulamalar için uygun hale getirir.

Julia'nın Xoshiro uygulaması, ana kaynaktan yeni sanal PRNG'ler tohumlayan bir toplu üretim moduna sahiptir ve SIMD kullanarak paralel olarak üretim yapar (yani, toplu akış birden fazla iç içe geçmiş xoshiro örneğinden oluşur). Sanal PRNG'ler, toplu isteğin karşılandığı anda atılır (ve yığın tahsisatına neden olmamalıdır).

Eğer bir tohum sağlanmazsa, rastgele üretilmiş bir tohum oluşturulur (sistemden entropi kullanılarak). Zaten mevcut bir `Xoshiro` nesnesini yeniden tohumlamak için [`seed!`](@ref) fonksiyonuna bakın.

!!! compat "Julia 1.11"
    Negatif bir tamsayı tohumunun geçmesi en az Julia 1.11 gerektirir.


# Örnekler

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
