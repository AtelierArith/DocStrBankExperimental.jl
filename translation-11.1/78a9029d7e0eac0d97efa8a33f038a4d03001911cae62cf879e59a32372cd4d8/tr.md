```
factorize(A)
```

`A`'nın türüne dayalı olarak uygun bir faktorizasyon hesaplar. `factorize`, `A`'nın genel bir matris olarak geçilip geçilmediğini kontrol eder ve simetrik/üçgen vb. olup olmadığını belirler. `factorize`, `A`'nın her bir elemanını kontrol ederek her özelliği doğrular/çürütür. Simetri/üçgen yapısını çürütmek için mümkün olan en kısa sürede duracaktır. Dönüş değeri, birden fazla sistemin verimli bir şekilde çözülmesi için yeniden kullanılabilir. Örneğin: `A=factorize(A); x=A\b; y=A\C`.

| `A`'nın Özellikleri       | faktorizasyon türü                          |
|:------------------------- |:------------------------------------------- |
| Pozitif belirli           | Cholesky (bkz. [`cholesky`](@ref))          |
| Yoğun Simetrik/Hermitian  | Bunch-Kaufman (bkz. [`bunchkaufman`](@ref)) |
| Seyrek Simetrik/Hermitian | LDLt (bkz. [`ldlt`](@ref))                  |
| Üçgen                     | Üçgen                                       |
| Diyagonal                 | Diyagonal                                   |
| Bidiagonal                | Bidiagonal                                  |
| Tridiagonal               | LU (bkz. [`lu`](@ref))                      |
| Simetrik reel tridiagonal | LDLt (bkz. [`ldlt`](@ref))                  |
| Genel kare                | LU (bkz. [`lu`](@ref))                      |
| Genel kare olmayan        | QR (bkz. [`qr`](@ref))                      |

Örneğin, `factorize` bir Hermitian pozitif belirli matris üzerinde çağrıldığında, `factorize` bir Cholesky faktorizasyonu döndürecektir.

# Örnekler

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factorize(A) # factorize, A'nın zaten faktörize olup olmadığını kontrol edecektir
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

Bu, artık diğer lineer cebir fonksiyonlarına (örneğin, özdeğer çözücüleri) geçirilebilecek bir `5×5 Bidiagonal{Float64}` döndürür; bu fonksiyonlar `Bidiagonal` türleri için özel yöntemler kullanacaktır.
