```
LogRecord
```

Speichert die Ergebnisse eines einzelnen Protokollereignisses. Felder:

  * `level`: das [`LogLevel`](@ref) der Protokollnachricht
  * `message`: der textliche Inhalt der Protokollnachricht
  * `_module`: das Modul des Protokollereignisses
  * `group`: die Protokollgruppe (standardmäßig der Name der Datei, die das Protokollereignis enthält)
  * `id`: die ID des Protokollereignisses
  * `file`: die Datei, die das Protokollereignis enthält
  * `line`: die Zeile innerhalb der Datei des Protokollereignisses
  * `kwargs`: alle Schlüsselwortargumente, die an das Protokollereignis übergeben wurden
