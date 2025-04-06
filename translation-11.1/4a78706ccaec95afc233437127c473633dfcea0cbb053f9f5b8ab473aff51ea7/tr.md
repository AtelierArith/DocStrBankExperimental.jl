```
UnitLowerTriangular(A::AbstractMatrix)
```

Matris `A`'nın bir `UnitLowerTriangular` görünümünü oluşturur. Böyle bir görünüm, `A`'nın [`eltype`](@ref) türünün [`oneunit`](@ref) değerine sahip bir diyagonal içerir.

# Örnekler

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitLowerTriangular(A)
3×3 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0   ⋅    ⋅
 4.0  1.0   ⋅
 7.0  8.0  1.0
```
