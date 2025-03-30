```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

Bir simetrik veya Hermit matris `A`'nın Bunch-Kaufman [^Bunch1977] faktorizasyonunu `P'*U*D*U'*P` veya `P'*L*D*L'*P` olarak hesaplayın; bu, `A`'da hangi üçgenin saklandığına bağlıdır ve bir [`BunchKaufman`](@ref) nesnesi döndürün. `A` karmaşık simetrik ise, `U'` ve `L'` karmaşık olmayan transpozları, yani `transpose(U)` ve `transpose(L)`'yi ifade eder.

Ayrıştırmayı yinelemek, `S.uplo`'ya bağlı olarak uygun olan `S.D`, `S.U` veya `S.L` bileşenlerini ve `S.p`'yi üretir.

Eğer `rook` `true` ise, rook pivotlama kullanılır. Eğer `rook` false ise, rook pivotlama kullanılmaz.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu ([`issuccess`](@ref) aracılığıyla) kullanıcıya aittir.

`BunchKaufman` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`size`](@ref), `\`, [`inv`](@ref), [`issymmetric`](@ref), [`ishermitian`](@ref), [`getindex`](@ref).

[^Bunch1977]: J R Bunch ve L Kaufman, Some stable methods for calculating inertia and solving symmetric linear systems, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

# Örnekler

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A, Symmetric(A) tarafından dahili olarak sarılır
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

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

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

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
