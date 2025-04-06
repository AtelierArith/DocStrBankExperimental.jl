```
eachslice(A::AbstractArray; dims, drop=true)
```

Erstellt ein [`Slices`](@ref) Objekt, das ein Array von Schnitten über die Dimensionen `dims` von `A` ist und Ansichten zurückgibt, die alle Daten aus den anderen Dimensionen in `A` auswählen. `dims` kann entweder eine ganze Zahl oder ein Tupel von ganzen Zahlen sein.

Wenn `drop = true` (der Standard), werden die äußeren `Slices` die inneren Dimensionen verwerfen, und die Anordnung der Dimensionen entspricht denen in `dims`. Wenn `drop = false`, haben die `Slices` die gleiche Dimensionalität wie das zugrunde liegende Array, wobei die inneren Dimensionen die Größe 1 haben.

Siehe [`stack`](@ref)`(slices; dims)` für die Umkehrung von `eachslice(A; dims::Integer)`.

Siehe auch [`eachrow`](@ref), [`eachcol`](@ref), [`mapslices`](@ref) und [`selectdim`](@ref).

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


!!! compat "Julia 1.9"
    Vor Julia 1.9 gab es einen Iterator zurück, und es wurde nur eine einzelne Dimension `dims` unterstützt.


# Beispiele

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
