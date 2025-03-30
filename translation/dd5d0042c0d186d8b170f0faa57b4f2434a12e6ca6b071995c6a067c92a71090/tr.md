```
Vector{T}(missing, m)
```

[`Vector{T}`](@ref) uzunluğunda `m` ile başlatılmış [`missing`](@ref) girişleri ile bir vektör oluşturur. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Missing <: T`.

# Örnekler

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
