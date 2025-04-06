```
unwatch_folder(pfad::AbstractString)
```

Stoppen Sie die Hintergrundverfolgung von Änderungen für `pfad`. Es wird nicht empfohlen, dies zu tun, während eine andere Aufgabe darauf wartet, dass `watch_folder` für denselben Pfad zurückkehrt, da das Ergebnis unvorhersehbar sein kann.
