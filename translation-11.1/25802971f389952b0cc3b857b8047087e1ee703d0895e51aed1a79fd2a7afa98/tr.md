```
nonmissingtype(T::Type)
```

Eğer `T`, `Missing` içeren bir türler birleşimiyse, `Missing` kaldırılmış yeni bir tür döndür.

# Örnekler

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! uyumluluk "Julia 1.3"
    Bu fonksiyon Julia 1.3 itibarıyla dışa aktarılmıştır.

