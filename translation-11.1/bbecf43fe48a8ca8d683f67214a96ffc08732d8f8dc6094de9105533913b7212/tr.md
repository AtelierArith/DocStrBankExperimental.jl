```
filter(f, d::AbstractDict)
```

`f`'nin `false` olduğu elemanları kaldırarak `d`'nin bir kopyasını döndürür. `f` fonksiyonuna `key=>value` çiftleri geçirilir.

# Örnekler

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} with 2 entries:
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} with 1 entry:
  1 => "a"
```
