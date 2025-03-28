```
Base.checked_neg(x)
```

Berechnet `-x` und überprüft auf Überlauf-Fehler, wo dies zutrifft. Zum Beispiel können standardmäßige vorzeichenbehaftete Ganzzahlen im Zweierkomplement (z. B. `Int`) `-typemin(Int)` nicht darstellen, was zu einem Überlauf führt.

Der Überlaufschutz kann eine spürbare Leistungseinbuße zur Folge haben.
