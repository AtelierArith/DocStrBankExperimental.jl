```
subtypes(T::DataType)
```

DataType `T`'nin doğrudan alt türlerinin bir listesini döndürür. Şu anda yüklenmiş olan tüm alt türler dahil edilir, bunlar mevcut modülde görünmeyenler de dahil.

Ayrıca bkz. [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref).

# Örnekler

```jldoctest
julia> subtypes(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
