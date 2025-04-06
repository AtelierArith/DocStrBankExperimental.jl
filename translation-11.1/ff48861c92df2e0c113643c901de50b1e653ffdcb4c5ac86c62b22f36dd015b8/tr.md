```
istextmime(m::MIME)
```

Bir MIME türünün metin verisi olup olmadığını belirleyin. MIME türlerinin, metin verisi olduğu bilinen bir dizi tür dışında, ikili veri olduğu varsayılmaktadır (muhtemelen Unicode).

# Örnekler

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
