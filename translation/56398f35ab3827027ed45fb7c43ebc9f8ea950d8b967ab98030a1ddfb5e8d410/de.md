```
@test_warn msg expr
```

Testen Sie, ob die Auswertung von `expr` zu einer [`stderr`](@ref)-Ausgabe führt, die den `msg`-String enthält oder mit dem `msg`-Regulären Ausdruck übereinstimmt. Wenn `msg` eine boolesche Funktion ist, wird getestet, ob `msg(output)` `true` zurückgibt. Wenn `msg` ein Tupel oder Array ist, wird überprüft, ob die Fehlermeldung jedes Element in `msg` enthält/übereinstimmt. Gibt das Ergebnis der Auswertung von `expr` zurück.

Siehe auch [`@test_nowarn`](@ref), um das Fehlen von Fehlermeldungen zu überprüfen.

Hinweis: Warnungen, die von `@warn` erzeugt werden, können mit diesem Makro nicht getestet werden. Verwenden Sie stattdessen [`@test_logs`](@ref).
