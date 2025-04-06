```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

Düzenli ifade `r`'nin `s` içindeki tüm eşleşmelerini arar ve eşleşmeler üzerinde bir yineleyici döndürür. Eğer `overlap` `true` ise, eşleşen diziler orijinal dizideki indeksleri örtüşmesine izin verilir, aksi takdirde farklı karakter aralıklarından olmalıdır.

# Örnekler

```jldoctest
julia> rx = r"a.a"
r"a.a"

julia> m = eachmatch(rx, "a1a2a3a")
Base.RegexMatchIterator{String}(r"a.a", "a1a2a3a", false)

julia> collect(m)
2-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a3a")

julia> collect(eachmatch(rx, "a1a2a3a", overlap = true))
3-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a2a")
 RegexMatch("a3a")
```
