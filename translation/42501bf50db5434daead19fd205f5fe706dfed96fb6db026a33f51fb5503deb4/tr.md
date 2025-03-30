```
isimmutable(v) -> Bool
```

!!! uyarı     Bunun yerine `!ismutable(v)` kullanmayı düşünün, çünkü `isimmutable(v)` gelecekteki bir sürümde `!ismutable(v)` ile değiştirilecektir. (Julia 1.5'ten beri)

Değer `v` eğer değiştirilemezse `true` döner. Değiştirilemezlik hakkında bir tartışma için [Mutable Composite Types](@ref) bölümüne bakın. Bu fonksiyon değerler üzerinde çalıştığı için, eğer bir tür verirseniz, `DataType` değerinin değiştirilebilir olduğunu size söyleyecektir.

# Örnekler

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
