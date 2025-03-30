```
tryparse(x::Union{AbstractString, IO})
tryparse(p::Parser, x::Union{AbstractString, IO})
```

Dizeyi veya akışı `x` ayrıştırın ve sonuçta oluşan tabloyu (sözlük) döndürün. Başarısızlık durumunda bir [`ParserError`](@ref) döndürün.

Ayrıca bkz. [`TOML.parse`](@ref).
