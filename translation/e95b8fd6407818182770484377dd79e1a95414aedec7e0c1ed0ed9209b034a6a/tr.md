```
eps(::Type{DateTime}) -> Millisaniye
eps(::Type{Date}) -> Gün
eps(::Type{Time}) -> Nan saniye
eps(::TimeType) -> Periyot
```

`TimeType` tarafından desteklenen en küçük birim değerini döndürür.

# Örnekler

```jldoctest
julia> eps(DateTime)
1 millisaniye

julia> eps(Date)
1 gün

julia> eps(Time)
1 nan saniye
```
