```
Vector{T}(nothing, m)
```

[`Vector{T}`](@ref) uzunluğunda `m` ile başlatılmış [`nothing`](@ref) girişleri ile bir vektör oluşturur. Eleman türü `T`, bu değerleri tutabilmelidir, yani `Nothing <: T`.

# Örnekler

```jldoctest
julia> Vector{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing
```
