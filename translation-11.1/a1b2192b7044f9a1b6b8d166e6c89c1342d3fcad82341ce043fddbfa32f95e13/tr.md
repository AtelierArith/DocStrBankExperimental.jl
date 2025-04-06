```
isposdef(A) -> Bool
```

Bir matrisin pozitif tanımlı (ve Hermit) olup olmadığını `A`'nın Cholesky faktörizasyonunu gerçekleştirmeye çalışarak test eder.

Ayrıca bkz. [`isposdef!`](@ref), [`cholesky`](@ref).

# Örnekler

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
