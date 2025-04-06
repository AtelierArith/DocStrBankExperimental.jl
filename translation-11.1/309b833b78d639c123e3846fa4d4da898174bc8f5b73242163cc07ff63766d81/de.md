```
record(ts::AbstractTestSet, res::Result)
```

Ein Ergebnis zu einem Testset aufzeichnen. Diese Funktion wird von der `@testset`-Infrastruktur jedes Mal aufgerufen, wenn ein enthaltenes `@test`-Makro abgeschlossen ist, und erhält das Testergebnis (das ein `Error` sein könnte). Dies wird auch mit einem `Error` aufgerufen, wenn eine Ausnahme innerhalb des Testblocks, aber außerhalb eines `@test`-Kontexts ausgelöst wird.
