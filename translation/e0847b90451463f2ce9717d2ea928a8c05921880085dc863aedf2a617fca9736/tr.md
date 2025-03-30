```
ismutable(v) -> Bool
```

Değer `v` değiştirilebilir ise yalnızca `true` döner. Değiştirilemezlik hakkında bir tartışma için [Mutable Composite Types](@ref) bölümüne bakın. Bu fonksiyon değerler üzerinde çalıştığı için, eğer bir `DataType` verirseniz, bu türdeki bir değerin değiştirilebilir olduğunu size söyleyecektir.

!!! not
    Teknik nedenlerden dolayı, `ismutable` belirli özel türlerin (örneğin `String` ve `Symbol`) değerleri için `true` döner, oysa bunlar izin verilen bir şekilde değiştirilemez.


Ayrıca [`isbits`](@ref), [`isstructtype`](@ref) bakın.

# Örnekler

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! uyumluluk "Julia 1.5"
    Bu fonksiyon en az Julia 1.5 gerektirir.


```
