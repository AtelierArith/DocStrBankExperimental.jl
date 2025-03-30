```
mul!(C, A, B, α, β) -> C
```

Birleştirilmiş yerinde matris-matris veya matris-vektör çarpma-toplama $A B α + C β$. Sonuç `C`'de saklanır ve üzerine yazılır. `C`'nin `A` veya `B` ile aynı olmaması gerektiğini unutmayın.

!!! compat "Julia 1.3"
    Beş argümanlı `mul!` en az Julia 1.3 gerektirir.


# Örnekler

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; C = [1.0 2.0; 3.0 4.0];

julia> α, β = 100.0, 10.0;

julia> mul!(C, A, B, α, β) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0

julia> C_original = [1.0 2.0; 3.0 4.0]; # C'nin orijinal değerinin bir kopyası

julia> C == A * B * α + C_original * β
true
```
