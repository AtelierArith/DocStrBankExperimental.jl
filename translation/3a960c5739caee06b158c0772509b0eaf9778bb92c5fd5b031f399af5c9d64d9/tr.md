```
UpperHessenberg(A::AbstractMatrix)
```

Matris `A`'nın bir `UpperHessenberg` görünümünü oluşturur. `A`'nın ilk alt diyagonalinin altındaki girişler göz ardı edilir.

!!! compat "Julia 1.3"
    Bu tür Julia 1.3'te eklendi.


`H \ b`, `det(H)` ve benzeri işlemler için verimli algoritmalar uygulanmıştır.

Benzer bir üst-Hessenberg matrisine herhangi bir matrisin faktörleştirilmesi için [`hessenberg`](@ref) fonksiyonuna da bakın.

Eğer `F::Hessenberg` faktörizasyon nesnesi ise, birim matris `F.Q` ile erişilebilir ve Hessenberg matrisi `F.H` ile erişilebilir. `Q` çıkarıldığında, sonuç türü `HessenbergQ` nesnesidir ve [`convert(Array, _)`](@ref) (veya kısaca `Array(_)`) ile normal bir matrise dönüştürülebilir.

Ayrıştırmayı yinelemek, `F.Q` ve `F.H` faktörlerini üretir.

# Örnekler

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
