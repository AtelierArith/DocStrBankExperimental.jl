```
@test_throws exception expr
```

`expr` ifadesinin `exception` fırlattığını test eder. İstisna, görüntülenen hata mesajında meydana gelen bir tür, bir dize, düzenli ifade veya dize listesini belirtebilir, bir eşleşme fonksiyonu veya bir değer (alanları karşılaştırarak eşitlik için test edilecektir) olabilir. `@test_throws`'ın bir son anahtar biçimini desteklemediğini unutmayın.

!!! compat "Julia 1.8"
    `exception` olarak bir tür veya değer dışında bir şey belirtme yeteneği, Julia v1.8 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> @test_throws BoundsError [1, 2, 3][4]
Test Passed
      Thrown: BoundsError

julia> @test_throws DimensionMismatch [1, 2, 3] + [1, 2]
Test Passed
      Thrown: DimensionMismatch

julia> @test_throws "Try sqrt(Complex" sqrt(-1)
Test Passed
     Message: "DomainError with -1.0:\nsqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x))."
```

Son örnekte, tek bir dize ile eşleşmek yerine alternatif olarak şu şekilde yapılabilirdi:

  * `["Try", "Complex"]` (bir dize listesi)
  * `r"Try sqrt\([Cc]omplex"` (bir düzenli ifade)
  * `str -> occursin("complex", str)` (bir eşleşme fonksiyonu)
