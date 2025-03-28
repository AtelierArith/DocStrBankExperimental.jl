```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

Sucht nach allen Übereinstimmungen des regulären Ausdrucks `r` in `s` und gibt einen Iterator über die Übereinstimmungen zurück. Wenn `overlap` `true` ist, dürfen die übereinstimmenden Sequenzen sich in den Indizes des ursprünglichen Strings überlappen, andernfalls müssen sie aus unterschiedlichen Zeichenbereichen stammen.

# Beispiele

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
