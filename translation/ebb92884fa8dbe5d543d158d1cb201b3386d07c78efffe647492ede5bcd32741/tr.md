```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

Düzenli ifade `r`'nin `s` içinde ilk eşleşmesini arar ve eşleşmeyi içeren bir [`RegexMatch`](@ref) nesnesi döner, ya da eşleşme başarısız olursa hiçbir şey döner. Eşleşen alt dizeye `m.match` ile erişerek ve yakalanan dizilere `m.captures` ile erişerek ulaşılabilir. İsteğe bağlı `idx` argümanı, aramaya başlamak için bir indeks belirtir.

# Örnekler

```jldoctest
julia> rx = r"a(.)a"
r"a(.)a"

julia> m = match(rx, "cabac")
RegexMatch("aba", 1="b")

julia> m.captures
1-element Vector{Union{Nothing, SubString{String}}}:
 "b"

julia> m.match
"aba"

julia> match(rx, "cabac", 3) === nothing
true
```
