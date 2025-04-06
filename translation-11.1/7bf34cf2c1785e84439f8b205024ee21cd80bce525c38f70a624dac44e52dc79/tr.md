```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

`A`'nın LU faktorizasyonunu hesaplayın.

`check = true` olduğunda, ayrıştırma başarısız olursa bir hata fırlatılır. `check = false` olduğunda, ayrıştırmanın geçerliliğini kontrol etme sorumluluğu ([`issuccess`](@ref) aracılığıyla) kullanıcıya aittir.

Varsayılan olarak, `check = true` ile, ayrıştırma geçerli faktörler ürettiğinde de bir hata fırlatılır, ancak üst üçgen faktör `U` sıralı eksiktir. Bu, `allowsingular = true` geçerek değiştirilebilir.

Çoğu durumda, `A`, `+`, `-`, `*` ve `/` destekleyen bir eleman türü `T` ile `AbstractMatrix{T}`'nin bir alt türü `S` ise, dönüş türü `LU{T,S{T}}`'dir.

Genel olarak, LU faktorizasyonu, matrisin satırlarının bir permütasyonunu içerir (aşağıda açıklanan `F.p` çıktısına karşılık gelen), "pivotlama" olarak bilinir (çünkü "pivot" olan, `F.U`'nun diyagonal girişi hangi satırın içerdiğini seçmekle ilgilidir). Aşağıdaki pivotlama stratejilerinden biri, isteğe bağlı `pivot` argümanı aracılığıyla seçilebilir:

  * `RowMaximum()` (varsayılan): standart pivotlama stratejisi; pivot, kalan, faktörleştirilecek satırlar arasında maksimum mutlak değere sahip elemana karşılık gelir. Bu pivotlama stratejisi, eleman türünün de [`abs`](@ref) ve [`<`](@ref) desteklemesini gerektirir. (Bu, genellikle kayan nokta matrisleri için tek sayısal olarak kararlı seçenektir.)
  * `RowNonZero()`: pivot, kalan, faktörleştirilecek satırlar arasında ilk sıfır olmayan elemana karşılık gelir. (Bu, el hesaplamalarında tipik seçime karşılık gelir ve [`iszero`](@ref) destekleyen ancak `abs` veya `<` desteklemeyen daha genel cebirsel sayı türleri için de yararlıdır.)
  * `NoPivot()`: pivotlama kapalı (bir pivot pozisyonunda sıfır girişi ile karşılaşılırsa başarısız olur, hatta `allowsingular = true` olsa bile).

Faktorizasyonun bireysel bileşenlerine [`getproperty`](@ref) aracılığıyla erişilebilir:

| Bileşen | Açıklama                       |
|:------- |:------------------------------ |
| `F.L`   | `LU`'nun `L` (alt üçgen) kısmı |
| `F.U`   | `LU`'nun `U` (üst üçgen) kısmı |
| `F.p`   | (sağ) permütasyon `Vector`     |
| `F.P`   | (sağ) permütasyon `Matrix`     |

Faktorizasyonu yinelemek, bileşenleri `F.L`, `F.U` ve `F.p` üretir.

`F` ile `A` arasındaki ilişki

`F.L*F.U == A[F.p, :]`

`F` ayrıca aşağıdaki işlevleri destekler:

| Desteklenen işlev   | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

!!! compat "Julia 1.11"
    `allowsingular` anahtar argümanı Julia 1.11'de eklendi.


# Örnekler

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L faktörü:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U faktörü:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # yineleme ile parçalama

julia> l == F.L && u == F.U && p == F.p
true

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L faktörü:
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
U faktörü (sıralı eksik):
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
