```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

`T` türünden elemanlar içeren `N`-boyutlu [`Array`](@ref) oluşturun, [`missing`](@ref) girişleri ile başlatılmıştır. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Missing <: T`.

# Örnekler

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing

julia> Array{Union{Missing, Int}}(missing, 2, 3)
2×3 Matrix{Union{Missing, Int64}}:
 missing  missing  missing
 missing  missing  missing
```
