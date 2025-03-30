```
abspath(path::AbstractString) -> String
```

Bir yolu, gerekli ise mevcut dizini ekleyerek mutlak bir yola dönüştürür. Ayrıca, yolu [`normpath`](@ref) gibi normalize eder.

# Örnekler

Eğer `JuliaExample` adında bir dizindeyseniz ve kullandığınız veri `JuliaExample` dizinine göre iki seviye yukarıda ise, şunu yazabilirsiniz:

```
abspath("../../data")
```

Bu, `"/home/JuliaUser/data/"` gibi bir yol verir.

Ayrıca [`joinpath`](@ref), [`pwd`](@ref), [`expanduser`](@ref) bakınız.
