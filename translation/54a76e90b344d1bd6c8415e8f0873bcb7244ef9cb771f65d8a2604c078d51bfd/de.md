```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

Schreiben Sie `data` im TOML-Syntax in den Stream `io`. Wenn das Schlüsselwort-Argument `sorted` auf `true` gesetzt ist, sortieren Sie Tabellen gemäß der Funktion, die durch das Schlüsselwort-Argument `by` angegeben ist. Wenn das Schlüsselwort-Argument `inline_tables` angegeben ist, sollte es eine Menge von Tabellen sein, die "inline" gedruckt werden sollen.

Die folgenden Datentypen werden unterstützt: `AbstractDict`, `AbstractVector`, `AbstractString`, `Integer`, `AbstractFloat`, `Bool`, `Dates.DateTime`, `Dates.Time`, `Dates.Date`. Beachten Sie, dass die Ganzzahlen und Fließkommazahlen in `Float64` und `Int64` konvertierbar sein müssen. Für andere Datentypen übergeben Sie die Funktion `to_toml`, die die Datentypen annimmt und einen Wert eines unterstützten Typs zurückgibt.
