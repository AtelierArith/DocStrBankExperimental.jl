```
stage(ie::IndexEntry) -> Cint
```

Holen Sie sich die Stufennummer von `ie`. Die Stufennummer `0` repräsentiert den aktuellen Zustand des Arbeitsbaums, aber andere Zahlen können im Falle eines Merge-Konflikts verwendet werden. In einem solchen Fall beschreiben die verschiedenen Stufennummern in einem `IndexEntry`, zu welcher Seite(n) des Konflikts der aktuelle Zustand der Datei gehört. Stufe `0` ist der Zustand vor dem versuchten Merge, Stufe `1` sind die Änderungen, die lokal vorgenommen wurden, Stufen `2` und höher sind für Änderungen von anderen Branches (zum Beispiel können im Falle eines Multi-Branch-"Oktopus"-Merges die Stufen `2`, `3` und `4` verwendet werden).
