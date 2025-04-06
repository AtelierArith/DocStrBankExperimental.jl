```
@test_nowarn expr
```

Testen Sie, ob die Auswertung von `expr` zu leerem [`stderr`](@ref) Ausgabe (keine Warnungen oder andere Nachrichten) führt. Gibt das Ergebnis der Auswertung von `expr` zurück.

Hinweis: Das Fehlen von Warnungen, die von `@warn` erzeugt werden, kann mit diesem Makro nicht getestet werden. Verwenden Sie stattdessen [`@test_logs`](@ref).
