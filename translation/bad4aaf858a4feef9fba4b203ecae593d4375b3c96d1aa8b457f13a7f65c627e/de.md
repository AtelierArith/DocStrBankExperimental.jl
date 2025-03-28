```
extract(
    [ predicate, ] tarball, [ dir ];
    [ skeleton = <none>, ]
    [ copy_symlinks = <auto>, ]
    [ set_permissions = true, ]
) -> dir

    predicate       :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    skeleton        :: Union{AbstractString, AbstractCmd, IO}
    copy_symlinks   :: Bool
    set_permissions :: Bool
```

Extrahieren Sie ein Tar-Archiv ("tarball"), das sich unter dem Pfad `tarball` befindet, in das Verzeichnis `dir`. Wenn `tarball` ein IO-Objekt anstelle eines Pfades ist, werden die Inhalte des Archivs aus diesem IO-Stream gelesen. Das Archiv wird in `dir` extrahiert, das entweder ein vorhandenes leeres Verzeichnis oder ein nicht vorhandener Pfad sein muss, der als neues Verzeichnis erstellt werden kann. Wenn `dir` nicht angegeben ist, wird das Archiv in ein temporäres Verzeichnis extrahiert, das von `extract` zurückgegeben wird.

Wenn eine `predicate`-Funktion übergeben wird, wird sie für jedes `Header`-Objekt aufgerufen, das beim Extrahieren von `tarball` begegnet, und der Eintrag wird nur extrahiert, wenn `predicate(hdr)` wahr ist. Dies kann verwendet werden, um selektiv nur Teile eines Archivs zu extrahieren, um Einträge zu überspringen, die dazu führen, dass `extract` einen Fehler auslöst, oder um aufzuzeichnen, was während des Extraktionsprozesses extrahiert wird.

Bevor es an die Prädikatsfunktion übergeben wird, wird das `Header`-Objekt etwas vom Rohheader im Tarball modifiziert: Das `path`-Feld wird normalisiert, um `.`-Einträge zu entfernen und mehrere aufeinanderfolgende Schrägstriche durch einen einzelnen Schrägstrich zu ersetzen. Wenn der Eintrag vom Typ `:hardlink` ist, wird der Zielpfad des Links auf die gleiche Weise normalisiert, damit er mit dem Pfad des Ziel-Eintrags übereinstimmt; das Größenfeld wird auf die Größe des Zielpfads gesetzt (der bereits gesehen worden sein muss).

Wenn das Schlüsselwort `skeleton` übergeben wird, wird ein "Skelett" des extrahierten Tarballs in die angegebene Datei oder IO-Handle geschrieben. Diese Skelettdatei kann verwendet werden, um einen identischen Tarball zu reproduzieren, indem das Schlüsselwort `skeleton` an die Funktion `create` übergeben wird. Die Argumente `skeleton` und `predicate` können nicht zusammen verwendet werden.

Wenn `copy_symlinks` `true` ist, werden anstelle von symbolischen Links diese als Kopien dessen extrahiert, auf was sie verweisen, wenn sie intern im Tarball sind und wenn dies möglich ist. Nicht-internale Symlinks, wie ein Link zu `/etc/passwd`, werden nicht kopiert. Symlinks, die in irgendeiner Weise zyklisch sind, werden ebenfalls nicht kopiert und stattdessen übersprungen. Standardmäßig erkennt `extract`, ob Symlinks in `dir` erstellt werden können oder nicht, und kopiert automatisch Symlinks, wenn sie nicht erstellt werden können.

Wenn `set_permissions` `false` ist, werden keine Berechtigungen für die extrahierten Dateien festgelegt.
