```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

Beginnen Sie mit der asynchronen Ausführung von `command` und geben Sie ein `process::IO`-Objekt zurück. Wenn `read` wahr ist, stammen die Lesevorgänge vom Standardausgang des Prozesses, und `stdio` gibt optional den Standard-Eingabestrom des Prozesses an. Wenn `write` wahr ist, gehen die Schreibvorgänge an den Standard-Eingabestrom des Prozesses, und `stdio` gibt optional den Standard-Ausgangsstrom des Prozesses an. Der Standard-Fehlerstrom des Prozesses ist mit dem aktuellen globalen `stderr` verbunden.
