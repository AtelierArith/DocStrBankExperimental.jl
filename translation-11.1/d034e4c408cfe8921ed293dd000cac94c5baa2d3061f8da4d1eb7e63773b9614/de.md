```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

Überwacht die Datei oder das Verzeichnis `path` auf Änderungen, bis eine Änderung auftritt oder `timeout_s` Sekunden vergangen sind. Diese Funktion pollt das Dateisystem nicht, sondern verwendet plattformspezifische Funktionen, um Benachrichtigungen vom Betriebssystem zu erhalten (z. B. über inotify unter Linux). Siehe die unten verlinkte NodeJS-Dokumentation für Details.

Der zurückgegebene Wert ist ein Objekt mit den booleschen Feldern `renamed`, `changed` und `timedout`, die das Ergebnis der Überwachung der Datei angeben.

Dieses Verhalten dieser Funktion variiert leicht zwischen den Plattformen. Siehe [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) für detailliertere Informationen.
