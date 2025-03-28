"     get*test*counts(::AbstractTestSet) -> TestCounts

Rekursive Funktion, die die Anzahl der Testergebnisse jedes Typs direkt im Testset zählt und die Gesamtzahlen über die untergeordneten Testsets summiert.

Benutzerdefinierte `AbstractTestSet` sollten diese Funktion implementieren, um ihre Gesamtzahlen zu zählen und zusammen mit `DefaultTestSet` anzuzeigen.

Wenn dies für ein benutzerdefiniertes `TestSet` nicht implementiert ist, fällt die Ausgabe auf die Berichterstattung von `x` für Fehler und `?s` für die Dauer zurück.
