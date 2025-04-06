```
getkey(koleksiyon, anahtar, varsayılan)
```

Anahtar `anahtar` ile eşleşen anahtarı `koleksiyon` içinde varsa döndür, aksi takdirde `varsayılan` döndür.

# Örnekler

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> getkey(D, 'a', 1)
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük)

julia> getkey(D, 'd', 'a')
'a': ASCII/Unicode U+0061 (kategori Ll: Harf, küçük)
```
