```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

Die `ArgWrite`-Typen sind eine Vereinigung der Typen, die die Funktion `arg_write` in beschreibbare IO-Handles umwandeln kann, mit Ausnahme von `Nothing`, das `arg_write` behandelt, indem es eine temporäre Datei erstellt. Siehe [`arg_write`](@ref) für Details.
