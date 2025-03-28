```
watch_folder(path::AbstractString, timeout_s::Real=-1)
```

Überwacht eine Datei oder ein Verzeichnis `path` auf Änderungen, bis eine Änderung aufgetreten ist oder `timeout_s` Sekunden vergangen sind. Diese Funktion pollt das Dateisystem nicht, sondern verwendet plattformspezifische Funktionen, um Benachrichtigungen vom Betriebssystem zu erhalten (z. B. über inotify unter Linux). Siehe die unten verlinkte NodeJS-Dokumentation für weitere Details.

Dies wird weiterhin Änderungen für `path` im Hintergrund verfolgen, bis `unwatch_folder` für dasselbe `path` aufgerufen wird.

Der zurückgegebene Wert ist ein Paar, bei dem das erste Feld der Name der geänderten Datei ist (sofern verfügbar) und das zweite Feld ein Objekt mit den booleschen Feldern `renamed`, `changed` und `timedout` ist, die das Ereignis angeben.

Dieses Verhalten dieser Funktion variiert leicht zwischen den Plattformen. Siehe [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) für detailliertere Informationen.
