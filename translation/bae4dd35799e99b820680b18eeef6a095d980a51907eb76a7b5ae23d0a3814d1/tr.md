```
UnionAll
```

Bir tür parametresi üzerindeki tüm değerlerin birleşimi. `UnionAll`, bazı parametrelerin değerlerinin bilinmediği parametrik türleri tanımlamak için kullanılır. [UnionAll Türleri](@ref) bölümüne bakın.

# Örnekler

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
