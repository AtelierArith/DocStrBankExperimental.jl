```
TestCounts
```

Hält den Zustand für das rekursive Sammeln der Ergebnisse eines Testsets zu Anzeigezwecken.

Felder:

  * `customized`: Ob die Funktion `get_test_counts` für das `AbstractTestSet` angepasst wurde, für das dieses Zählobjekt gedacht ist. Wenn eine benutzerdefinierte Methode definiert wurde, immer `true` an den Konstruktor übergeben.
  * `passes`: Die Anzahl der bestandenen `@test`-Aufrufe.
  * `fails`: Die Anzahl der fehlgeschlagenen `@test`-Aufrufe.
  * `errors`: Die Anzahl der fehlerhaften `@test`-Aufrufe.
  * `broken`: Die Anzahl der defekten `@test`-Aufrufe.
  * `passes`: Die kumulierte Anzahl der bestandenen `@test`-Aufrufe.
  * `fails`: Die kumulierte Anzahl der fehlgeschlagenen `@test`-Aufrufe.
  * `errors`: Die kumulierte Anzahl der fehlerhaften `@test`-Aufrufe.
  * `broken`: Die kumulierte Anzahl der defekten `@test`-Aufrufe.
  * `duration`: Die Gesamtdauer, die das betreffende `AbstractTestSet` lief, als formatierter `String`.
