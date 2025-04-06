```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

Rastgele sayı üreteciyi yeniden tohumlayın: `rng`, yalnızca bir `seed` sağlandığında yeniden üretilebilir bir sayı dizisi verecektir. Bazı RNG'ler, `RandomDevice` gibi, bir tohum kabul etmez. `seed!` çağrısından sonra, `rng`, aynı tohumla başlatılmış yeni bir nesne ile eşdeğerdir. Kabul edilen tohumların türleri `rng` türüne bağlıdır, ancak genel olarak, tam sayı tohumları çalışmalıdır.

Eğer `rng` belirtilmemişse, paylaşılan görev yerel üretecin durumunu tohumlamayı varsayılan olarak alır.

# Örnekler

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # yeniden üretilebilir değil
true

julia> rand(Random.seed!(rng), Bool) # yeniden üretilebilir değil
false

julia> rand(Xoshiro(), Bool) # yeniden üretilebilir değil
true
```
