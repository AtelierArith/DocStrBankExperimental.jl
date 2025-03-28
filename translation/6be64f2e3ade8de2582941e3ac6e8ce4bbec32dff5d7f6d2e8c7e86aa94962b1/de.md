```
lstat(datei)
```

Wie [`stat`](@ref), aber für symbolische Links erhält die Funktion die Informationen für den Link selbst anstelle der Datei, auf die verwiesen wird. Diese Funktion muss auf einem Dateipfad und nicht auf einem Dateiobjekt oder einem Dateideskriptor aufgerufen werden.
