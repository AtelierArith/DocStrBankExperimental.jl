```
Regex(pattern[, flags]) <: AbstractPattern
```

Ein Typ, der einen regulären Ausdruck darstellt. `Regex`-Objekte können verwendet werden, um Zeichenfolgen mit [`match`](@ref) zu vergleichen.

`Regex`-Objekte können mit dem [`@r_str`](@ref) String-Makro erstellt werden. Der Konstruktor `Regex(pattern[, flags])` wird normalerweise verwendet, wenn der `pattern`-String interpoliert werden muss. Siehe die Dokumentation des String-Makros für Details zu den Flags.

!!! note
    Um interpolierte Variablen zu escapen, verwenden Sie `\Q` und `\E` (z. B. `Regex("\\Q$x\\E")`)

