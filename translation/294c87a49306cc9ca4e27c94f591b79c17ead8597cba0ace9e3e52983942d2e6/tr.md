```
küçükharf(c::AbstractChar)
```

`c`'yi küçük harfe dönüştür.

Ayrıca bkz. [`büyükharf`](@ref), [`başharf`](@ref).

# Örnekler

```jldoctest
julia> küçükharf('A')
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük harf)

julia> küçükharf('Ö')
'ö': Unicode U+00F6 (kategori Ll: Harf, küçük harf)
```
