```
Sampler(rng, x, repetition = Val(Inf))
```

`rng` için `x`'den rastgele değerler üretmek için kullanılabilecek bir örnekleyici nesnesi döndürür.

`sp = Sampler(rng, x, repetition)` olduğunda, rastgele değerler çekmek için `rand(rng, sp)` kullanılacak ve buna göre tanımlanmalıdır.

`repetition` `Val(1)` veya `Val(Inf)` olabilir ve uygulanabilir olduğunda ön hesaplama miktarını belirlemek için bir öneri olarak kullanılmalıdır.

[`Random.SamplerType`](@ref) ve [`Random.SamplerTrivial`](@ref) varsayılan geri dönüşlerdir *tipler* ve *değerler* için, sırasıyla. [`Random.SamplerSimple`](@ref) yalnızca bu amaç için ekstra türler tanımlamadan önceden hesaplanmış değerleri saklamak için kullanılabilir.
