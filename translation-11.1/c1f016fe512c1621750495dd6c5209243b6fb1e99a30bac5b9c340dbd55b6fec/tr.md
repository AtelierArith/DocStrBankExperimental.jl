```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Geçilen kümelerin [`union`](@ref) birleşimini oluşturur ve `s`'yi sonuçla günceller. Dizilerle sıralamayı korur.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} with 5 elements:
  5
  4
  7
  3
  1
```
