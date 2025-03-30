```
isposdef!(A) -> Bool
```

Bir matrisin pozitif tanımlı (ve Hermit) olup olmadığını, `A` üzerinde Cholesky faktörizasyonu yapmaya çalışarak test eder, bu süreçte `A`'yı üzerine yazar. Ayrıca [`isposdef`](@ref) bakınız.

# Örnekler

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
