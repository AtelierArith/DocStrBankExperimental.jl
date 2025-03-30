```
haskey(koleksiyon, anahtar) -> Bool
```

Bir koleksiyonun belirli bir `anahtar` için bir eşleme olup olmadığını belirleyin.

# Örnekler

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
