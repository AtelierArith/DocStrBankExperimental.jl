```
muladd(A, y, z)
```

Birleşik çarpma-toplama, `A*y .+ z`, matris-matris veya matris-vektör çarpımı için. Sonuç her zaman `A*y` ile aynı boyuttadır, ancak `z` daha küçük olabilir veya bir skalar olabilir.

!!! compat "Julia 1.6"
    Bu yöntemler Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> A=[1.0 2.0; 3.0 4.0]; B=[1.0 1.0; 1.0 1.0]; z=[0, 100];

julia> muladd(A, B, z)
2×2 Matrix{Float64}:
   3.0    3.0
 107.0  107.0
```
