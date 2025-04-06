```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

Bir matris veya vektör `A`'nın sütunlarının bir vektörü olan bir [`ColumnSlices`](@ref) nesnesi oluşturur. Sütun dilimleri, `A`'nın `AbstractVector` görünümleri olarak döndürülür.

Tersi için [`stack`](@ref)`(cols)` veya `reduce(`[`hcat`](@ref)`, cols)`'a bakın.

Ayrıca [`eachrow`](@ref), [`eachslice`](@ref) ve [`mapslices`](@ref) ile de ilgilidir.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


!!! compat "Julia 1.9"
    Julia 1.9'dan önce, bu bir iteratör döndürüyordu.


# Örnekler

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> s = eachcol(a)
2-element ColumnSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
 [1, 3]
 [2, 4]

julia> s[1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3
```
