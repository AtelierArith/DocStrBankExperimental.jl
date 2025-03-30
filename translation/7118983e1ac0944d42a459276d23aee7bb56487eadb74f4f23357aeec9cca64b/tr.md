```
mul!(Y, A, B) -> Y
```

Matris-matris veya matris-vektör çarpımını $A B$ hesaplar ve sonucu `Y`'de saklar, mevcut `Y` değerini geçersiz kılar. `Y`'nin `A` veya `B` ile aynı referansı taşımaması gerektiğini unutmayın.

# Örnekler

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; Y = similar(B);

julia> mul!(Y, A, B) === Y
true

julia> Y
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0

julia> Y == A * B
true
```

# Uygulama

Özel matris ve vektör türleri için, mümkünse 3-argümanlı `mul!`'yi doğrudan uygulamak yerine 5-argümanlı `mul!`'yi uygulamanız önerilir.
