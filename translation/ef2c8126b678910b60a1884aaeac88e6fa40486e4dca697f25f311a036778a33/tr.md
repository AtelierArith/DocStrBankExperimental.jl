```
Matrix{T}(missing, m, n)
```

`m`×`n` boyutunda, [`missing`](@ref) girişleri ile başlatılmış bir [`Matrix{T}`](@ref) oluşturur. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Missing <: T` olmalıdır.

# Örnekler

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
