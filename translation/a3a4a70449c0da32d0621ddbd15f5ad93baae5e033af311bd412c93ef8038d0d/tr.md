```
angle(z)
```

Bir karmaşık sayı `z`'nin radyan cinsinden faz açısını hesaplar.

`-pi ≤ angle(z) ≤ pi` aralığında bir sayı döndürür ve bu nedenle negatif reel eksen boyunca kesintilidir.

Ayrıca bakınız: [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# Örnekler

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 + 1e-20im))
180.0

julia> rad2deg(angle(-1 - 1e-20im))
-180.0
```
