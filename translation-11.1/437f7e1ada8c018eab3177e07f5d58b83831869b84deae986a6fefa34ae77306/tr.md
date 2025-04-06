```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

Dosya `f`'yi ayrıştır ve sonuçta oluşan tabloyu (sözlük) döndür. Başarısızlık durumunda bir [`ParserError`](@ref) fırlat.

Ayrıca bkz. [`TOML.tryparsefile`](@ref).
