```
cbrt(A::AbstractMatrix{<:Real})
```

Gerçek değerli bir matris `A`'nın gerçek değerli küp kökünü hesaplar. Eğer `T = cbrt(A)` ise, o zaman `T*T*T ≈ A` olur, aşağıda verilen örneğe bakınız.

Eğer `A` simetrikse, yani `HermOrSym{<:Real}` türündeyse, o zaman ([`eigen`](@ref)) küp kökü bulmak için kullanılır. Aksi takdirde, küp kökünü hesaplamak için gerçek değerli Schur ayrıştırmasını ([`schur`](@ref)) kullanan p-inci kök algoritmasının özel bir versiyonu [^S03] kullanılmaktadır.

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# Örnekler

```jldoctest
julia> A = [0.927524 -0.15857; -1.3677 -1.01172]
2×2 Matrix{Float64}:
  0.927524  -0.15857
 -1.3677    -1.01172

julia> T = cbrt(A)
2×2 Matrix{Float64}:
  0.910077  -0.151019
 -1.30257   -0.936818

julia> T*T*T ≈ A
true
```
