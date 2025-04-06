```
Base.checked_abs(x)
```

Berechnet `abs(x)` und überprüft auf Überlauf-Fehler, wo dies zutrifft. Zum Beispiel können standardmäßige vorzeichenbehaftete Ganzzahlen im Zweierkomplement (z. B. `Int`) `abs(typemin(Int))` nicht darstellen, was zu einem Überlauf führt.

Der Überlaufschutz kann eine spürbare Leistungseinbuße zur Folge haben.
