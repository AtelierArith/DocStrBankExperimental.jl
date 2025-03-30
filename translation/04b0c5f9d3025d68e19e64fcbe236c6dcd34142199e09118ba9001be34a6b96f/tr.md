```
filter!(f, d::AbstractDict)
```

`d`'yi güncelleyin, `f`'nin `false` olduğu elemanları kaldırın. `f` fonksiyonu `anahtar=>değer` çiftlerini alır.

# Örnekler

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} with 3 entries:
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} with 2 entries:
  3 => "c"
  1 => "a"
```
