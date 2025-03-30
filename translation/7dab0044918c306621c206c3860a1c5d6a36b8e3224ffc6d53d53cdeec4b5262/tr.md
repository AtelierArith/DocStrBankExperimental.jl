```
uppercase(c::AbstractChar)
```

`c`'yi büyük harfe dönüştür.

Ayrıca bkz. [`lowercase`](@ref), [`titlecase`](@ref).

# Örnekler

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (kategori Lu: Harf, büyük harf)

julia> uppercase('ê')
'Ê': Unicode U+00CA (kategori Lu: Harf, büyük harf)
```
