```
tempdir()
```

Erhält den Pfad des temporären Verzeichnisses. Unter Windows verwendet `tempdir()` die erste Umgebungsvariable, die in der geordneten Liste `TMP`, `TEMP`, `USERPROFILE` gefunden wird. Auf allen anderen Betriebssystemen verwendet `tempdir()` die erste Umgebungsvariable, die in der geordneten Liste `TMPDIR`, `TMP`, `TEMP` und `TEMPDIR` gefunden wird. Wenn keine dieser Variablen gefunden wird, wird der Pfad `"/tmp"` verwendet.
