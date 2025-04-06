```
Matrix{T}(nothing, m, n)
```

`m`×`n` boyutunda, [`nothing`](@ref) girişleri ile başlatılmış bir [`Matrix{T}`](@ref) oluşturur. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Nothing <: T`.

# Örnekler

```jldoctest
julia> Matrix{Union{Nothing, String}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
