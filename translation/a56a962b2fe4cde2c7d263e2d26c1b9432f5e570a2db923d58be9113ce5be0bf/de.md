```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

Geben Sie eine Markdown-Tabelle zurück, die Informationen über öffentliche globale Variablen in einem Modul bereitstellt, optional beschränkt auf diejenigen, die mit `pattern` übereinstimmen.

Die Schätzung des Speicherverbrauchs ist eine ungefähre Untergrenze für die Größe der internen Struktur des Objekts.

  * `all` : listet auch nicht-öffentliche Objekte auf, die im Modul definiert sind, veraltete Objekte und vom Compiler generierte Objekte.
  * `imported` : listet auch Objekte auf, die explizit aus anderen Modulen importiert wurden.
  * `recursive` : schließt rekursiv Objekte in Untermodulen ein und beachtet dabei die gleichen Einstellungen in jedem.
  * `sortby` : die Spalte, nach der die Ergebnisse sortiert werden sollen. Optionen sind `:name` (Standard), `:size` und `:summary`.
  * `minsize` : schließt nur Objekte mit einer Größe von mindestens `minsize` Bytes ein. Standardmäßig `0`.

Die Ausgabe von `varinfo` ist nur für Anzeigezwecke gedacht. Siehe auch [`names`](@ref), um ein Array von Symbolen zu erhalten, die in einem Modul definiert sind und für allgemeinere Manipulationen geeignet sind.
