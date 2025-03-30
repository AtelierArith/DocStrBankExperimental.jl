```
UnitUpperTriangular(A::AbstractMatrix)
```

Matris `A`'nın bir `UnitUpperTriangular` görünümünü oluşturur. Böyle bir görünüm, `A`'nın [`eltype`](@ref) türünün [`oneunit`](@ref) değerine sahip bir diyagonal içerir.

# Örnekler

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitUpperTriangular(A)
3×3 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  2.0  3.0
  ⋅   1.0  6.0
  ⋅    ⋅   1.0
```
