```
UnitRange{T<:Gerçek}
```

`start` ve `stop` türünde `T` ile parametrelenmiş bir aralık, `start`'tan başlayarak `stop` aşılana kadar `1` aralıklarla doldurulmuş elemanlarla. `a:b` sözdizimi, hem `a` hem de `b` `Tam Sayı` olduğunda bir `UnitRange` oluşturur.

# Örnekler

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
