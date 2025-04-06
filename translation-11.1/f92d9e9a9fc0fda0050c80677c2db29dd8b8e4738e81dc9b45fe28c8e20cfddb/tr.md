```
tryparsefile(f::AbstractString)
tryparsefile(p::Parser, f::AbstractString)
```

Dosya `f`'yi ayrıştır ve sonuçta oluşan tabloyu (sözlük) döndür. Başarısızlık durumunda bir [`ParserError`](@ref) döndür.

Ayrıca bkz. [`TOML.parsefile`](@ref).
