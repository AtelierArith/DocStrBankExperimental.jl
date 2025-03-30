```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

Dizeyi `x` dize veya akışını ayrıştırın ve sonuçta oluşan tabloyu (sözlük) döndürün. Başarısızlık durumunda bir [`ParserError`](@ref) fırlatın.

Ayrıca bkz. [`TOML.tryparse`](@ref).
