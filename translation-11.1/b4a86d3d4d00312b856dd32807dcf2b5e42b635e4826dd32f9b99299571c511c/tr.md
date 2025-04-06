```
hessenberg(A) -> Hessenberg
```

`A`'n Hessenberg ayrıştırmasını hesaplayın ve bir `Hessenberg` nesnesi döndürün. `F` faktörizasyon nesnesi ise, birim matris `F.Q` (tipi `LinearAlgebra.HessenbergQ`) ile ve Hessenberg matris `F.H` (tipi [`UpperHessenberg`](@ref)) ile erişilebilir; bunların her biri `Matrix(F.H)` veya `Matrix(F.Q)` ile normal bir matrise dönüştürülebilir.

Eğer `A` [`Hermitian`](@ref) veya gerçek-[`Symmetric`](@ref) ise, o zaman Hessenberg ayrıştırması gerçek-simetrik tridiagonal bir matris üretir ve `F.H` tipi [`SymTridiagonal`](@ref) olur.

Kaydırılmış faktörizasyon `A+μI = Q (H+μI) Q'` verimli bir şekilde `F + μ*I` kullanılarak oluşturulabilir; burada [`UniformScaling`](@ref) nesnesi [`I`](@ref) yeni bir `Hessenberg` nesnesi oluşturur ve paylaşılan depolama ile değiştirilmiş bir kaydırma sağlar. Verilen bir `F` için kaydırma `F.μ` ile elde edilir. Bu, `F` oluşturulduktan sonra farklı `μ` ve/veya `b` için birden fazla kaydırılmış çözüm `(F + μ*I) \ b`'nin verimli bir şekilde gerçekleştirilebilmesi açısından faydalıdır.

Ayrıştırmayı yinelemek, faktörleri `F.Q, F.H, F.μ` üretir.

# Örnekler

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q faktörü: 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H faktörü:
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # yineleme ile parçalama

julia> q == F.Q && h == F.H
true
```
