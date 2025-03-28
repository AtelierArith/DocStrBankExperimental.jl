```
tempname(parent=tempdir(); cleanup=true) -> String
```

Generiert einen temporären Dateipfad. Diese Funktion gibt nur einen Pfad zurück; es wird keine Datei erstellt. Der Pfad wird wahrscheinlich einzigartig sein, aber dies kann aufgrund der sehr geringen Möglichkeit, dass zwei gleichzeitige Aufrufe von `tempname` denselben Dateinamen generieren, nicht garantiert werden. Der Name wird garantiert von allen Dateien abzuweichen, die zum Zeitpunkt des Aufrufs von `tempname` bereits existieren.

Wenn ohne Argumente aufgerufen, wird der temporäre Name ein absoluter Pfad zu einem temporären Namen im temporären Verzeichnis des Systems sein, wie von `tempdir()` angegeben. Wenn ein `parent`-Verzeichnisargument angegeben wird, befindet sich der temporäre Pfad stattdessen in diesem Verzeichnis.

Die `cleanup`-Option steuert, ob der Prozess versucht, den zurückgegebenen Pfad automatisch zu löschen, wenn der Prozess beendet wird. Beachten Sie, dass die Funktion `tempname` an dem zurückgegebenen Ort keine Datei oder kein Verzeichnis erstellt, sodass es nichts zu bereinigen gibt, es sei denn, Sie erstellen dort eine Datei oder ein Verzeichnis. Wenn Sie dies tun und `cleanup` `true` ist, wird es bei der Beendigung des Prozesses gelöscht.

!!! compat "Julia 1.4"
    Die Argumente `parent` und `cleanup` wurden in 1.4 hinzugefügt. Vor Julia 1.4 wurde der Pfad von `tempname` niemals bei der Beendigung des Prozesses bereinigt.


!!! warning
    Dies kann zu Sicherheitslücken führen, wenn ein anderer Prozess denselben Dateinamen erhält und die Datei erstellt, bevor Sie dazu in der Lage sind. Öffnen Sie die Datei mit `JL_O_EXCL`, wenn dies ein Anliegen ist. Es wird auch empfohlen, stattdessen [`mktemp()`](@ref) zu verwenden.

