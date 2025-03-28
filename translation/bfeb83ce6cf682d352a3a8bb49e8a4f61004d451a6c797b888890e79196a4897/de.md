```
@__FILE__ -> String
```

Erweitert zu einem String mit dem Pfad zur Datei, die den Makroaufruf enthält, oder einem leeren String, wenn es durch `julia -e <expr>` ausgewertet wurde. Gibt `nothing` zurück, wenn dem Makro Informationen zur Parserquelle fehlen. Alternativ siehe [`PROGRAM_FILE`](@ref).
