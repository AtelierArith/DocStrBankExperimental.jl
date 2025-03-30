```
randstring([rng=default_rng()], [chars], [len=8])
```

`len` uzunluğunda, varsayılan olarak büyük ve küçük harfler ile 0-9 rakamlarından oluşan `chars` karakter setinden oluşan rastgele bir dize oluşturur. İsteğe bağlı `rng` argümanı, bir rastgele sayı üreteci belirtir, bkz. [Rastgele Sayılar](@ref).

# Örnekler

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! not
    `chars`, [`rand`](@ref) karakterleri rastgele seçebiliyorsa, `Char` veya `UInt8` türünde herhangi bir karakter koleksiyonu olabilir (daha verimli).

