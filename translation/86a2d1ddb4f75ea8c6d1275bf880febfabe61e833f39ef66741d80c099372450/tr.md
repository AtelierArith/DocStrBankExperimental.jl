```
eachrow(A::AbstractVecOrMat) <: AbstractVector
```

Bir matris veya vektör `A`'nın satırlarının bir vektörü olan bir [`RowSlices`](@ref) nesnesi oluşturur. Satır dilimleri, `A`'nın `AbstractVector` görünümleri olarak döndürülür.

Tersi için, [`stack`](@ref)`(rows; dims=1)`'e bakın.

Ayrıca [`eachcol`](@ref), [`eachslice`](@ref) ve [`mapslices`](@ref) ile de ilgilidir.

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

julia> s = eachrow(a)
2-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2]
 [3, 4]

julia> s[1]
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
```
