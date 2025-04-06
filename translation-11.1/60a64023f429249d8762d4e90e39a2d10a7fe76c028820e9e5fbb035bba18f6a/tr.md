```
titlecase(c::AbstractChar)
```

`c`'yi başlık durumuna dönüştür. Bu, çift harfler için büyük harften farklı olabilir, aşağıdaki örneği karşılaştırın.

Ayrıca bkz. [`uppercase`](@ref), [`lowercase`](@ref).

# Örnekler

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (kategori Lu: Harf, büyük harf)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (kategori Lt: Harf, başlık durumu)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (kategori Lu: Harf, büyük harf)
```
