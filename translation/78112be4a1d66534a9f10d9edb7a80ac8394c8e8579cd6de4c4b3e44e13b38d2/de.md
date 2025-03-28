```
create(
    [ predicate, ] dir, [ tarball ];
    [ skeleton, ] [ portable = false ]
) -> tarball

    predicate :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    skeleton  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

Erstellen Sie ein Tar-Archiv ("tarball") des Verzeichnisses `dir`. Das resultierende Archiv wird an den Pfad `tarball` geschrieben oder, wenn kein Pfad angegeben ist, wird ein temporärer Pfad erstellt und von dem Funktionsaufruf zurückgegeben. Wenn `tarball` ein IO-Objekt ist, wird der Inhalt des Tarballs stattdessen an diesen Handle geschrieben (der Handle bleibt offen).

Wenn eine `predicate`-Funktion übergeben wird, wird sie für jeden Systempfad aufgerufen, der beim rekursiven Durchsuchen von `dir` gefunden wird, und `path` wird nur in den Tarball aufgenommen, wenn `predicate(path)` wahr ist. Wenn `predicate(path)` für ein Verzeichnis falsch zurückgibt, wird das Verzeichnis vollständig ausgeschlossen: Nichts unter diesem Verzeichnis wird im Archiv enthalten sein.

Wenn das Schlüsselwort `skeleton` übergeben wird, wird die angegebene Datei oder IO-Handle als "Skelett" verwendet, um den Tarball zu generieren. Sie erstellen eine Skelettdatei, indem Sie das Schlüsselwort `skeleton` an den `extract`-Befehl übergeben. Wenn `create` mit dieser Skelettdatei aufgerufen wird und die extrahierten Dateien sich nicht geändert haben, wird ein identischer Tarball neu erstellt. Die Argumente `skeleton` und `predicate` können nicht zusammen verwendet werden.

Wenn das Flag `portable` wahr ist, werden die Pfadnamen auf Gültigkeit unter Windows überprüft, was sicherstellt, dass sie keine illegalen Zeichen enthalten oder Namen haben, die reserviert sind. Siehe https://stackoverflow.com/a/31976060/659248 für Details.
