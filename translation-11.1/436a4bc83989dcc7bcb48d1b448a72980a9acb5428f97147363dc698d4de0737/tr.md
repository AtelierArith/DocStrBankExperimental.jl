```
eachslice(A::AbstractArray; dims, drop=true)
```

Bir [`Slices`](@ref) nesnesi oluşturur; bu nesne, `A`'nın `dims` boyutları üzerindeki dilimlerin bir dizisidir ve `A`'daki diğer boyutlardan tüm verileri seçen görünümler döndürür. `dims` ya bir tamsayı ya da tamsayılar tuple'ı olabilir.

Eğer `drop = true` (varsayılan), dıştaki `Slices` iç boyutları atar ve boyutların sıralaması `dims`'deki gibi olur. Eğer `drop = false` ise, `Slices` temel dizinin aynı boyutluluğuna sahip olur ve iç boyutların boyutu 1'dir.

`eachslice(A; dims::Integer)`'ın tersini görmek için [`stack`](@ref)`(slices; dims)`'e bakın.

Ayrıca [`eachrow`](@ref), [`eachcol`](@ref), [`mapslices`](@ref) ve [`selectdim`](@ref) ile de ilgilidir.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


!!! compat "Julia 1.9"
    Julia 1.9'dan önce, bu bir iteratör döndürüyordu ve yalnızca tek bir boyut `dims` destekleniyordu.


# Örnekler

```jldoctest
julia> m = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> s = eachslice(m, dims=1)
3-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]

julia> s[1]
3-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
 3

julia> eachslice(m, dims=1, drop=false)
3×1 Slices{Matrix{Int64}, Tuple{Int64, Colon}, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}, 2}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]
```
