```
Array{T}(nothing, dims)
Array{T,N}(nothing, dims)
```

`T` türünden elemanlar içeren `N`-boyutlu [`Array`](@ref) oluşturun, [`nothing`](@ref) girişleri ile başlatılmıştır. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Nothing <: T`.

# Örnekler

```jldoctest
julia> Array{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing

julia> Array{Union{Nothing, Int}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, Int64}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
