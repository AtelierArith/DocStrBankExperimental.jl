```
BunchKaufman <: Factorization
```

Simetrik veya Hermit bir matris `A` için Bunch-Kaufman faktorizasyonunun matris faktorizasyon türü `P'UDU'P` veya `P'LDL'P` şeklindedir; bu, `A`'da üst (varsayılan) veya alt üçgenin saklanıp saklanmadığına bağlıdır. Eğer `A` karmaşık simetrik ise, `U'` ve `L'` karmaşık olmayan transpozları, yani sırasıyla `transpose(U)` ve `transpose(L)` anlamına gelir. Bu, [`bunchkaufman`](@ref) fonksiyonunun dönüş türüdür.

Eğer `S::BunchKaufman` faktorizasyon nesnesi ise, bileşenler `S.D`, `S.U` veya `S.L` aracılığıyla, `S.uplo` ve `S.p`'ye bağlı olarak elde edilebilir.

Ayrıştırmayı yinelemek, `S.D`, `S.U` veya `S.L` bileşenlerini, `S.uplo` ve `S.p`'ye bağlı olarak üretir.

# Örnekler

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A, içsel olarak Symmetric(A) ile sarılır
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D faktörü:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U faktörü:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
permutasyon:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # yineleme ile parçalama

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D faktörü:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L faktörü:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
permutasyon:
2-element Vector{Int64}:
 2
 1
```
