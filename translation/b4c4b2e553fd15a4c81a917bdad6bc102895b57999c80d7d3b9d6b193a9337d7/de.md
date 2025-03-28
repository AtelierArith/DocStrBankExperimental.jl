```
Parser()
```

Konstruktor für einen TOML `Parser`. Beachten Sie, dass man in den meisten Fällen keinen `Parser` explizit erstellen muss, sondern stattdessen direkt [`TOML.parsefile`](@ref) oder [`TOML.parse`](@ref) verwendet. Die Verwendung eines expliziten Parsers wird jedoch einige interne Datenstrukturen wiederverwenden, was für die Leistung vorteilhaft sein kann, wenn eine größere Anzahl kleiner Dateien geparst wird.
