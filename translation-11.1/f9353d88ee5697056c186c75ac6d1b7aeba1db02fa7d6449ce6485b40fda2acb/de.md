```
rewrite(
    [ predicate, ] old_tarball, [ new_tarball ];
    [ portable = false, ]
) -> new_tarball

    predicate   :: Header --> Bool
    old_tarball :: Union{AbstractString, AbstractCmd, IO}
    new_tarball :: Union{AbstractString, AbstractCmd, IO}
    portable    :: Bool
```

Schreibt `old_tarball` im Standardformat um, das `create` erzeugt, während gleichzeitig überprüft wird, dass es nichts enthält, was `extract` dazu bringen würde, einen Fehler auszulösen. Dies ist funktional äquivalent zu

```
Tar.create(Tar.extract(predicate, old_tarball), new_tarball)
```

Es extrahiert jedoch niemals etwas auf die Festplatte und verwendet stattdessen die Funktion `seek`, um durch die Daten des alten Tarballs zu navigieren. Wenn kein `new_tarball`-Argument übergeben wird, wird der neue Tarball in eine temporäre Datei geschrieben, deren Pfad zurückgegeben wird.

Wenn eine `predicate`-Funktion übergeben wird, wird sie für jedes `Header`-Objekt aufgerufen, das beim Extrahieren von `old_tarball` begegnet, und der Eintrag wird übersprungen, es sei denn, `predicate(hdr)` ist wahr. Dies kann verwendet werden, um selektiv nur Teile eines Archivs umzuschreiben, um Einträge zu überspringen, die dazu führen würden, dass `extract` einen Fehler auslöst, oder um aufzuzeichnen, welcher Inhalt während des Umschreibvorgangs begegnet wird.

Bevor es an die Prädikatsfunktion übergeben wird, wird das `Header`-Objekt etwas von der rohen Kopfzeile im Tarball modifiziert: Das `path`-Feld wird normalisiert, um `.`-Einträge zu entfernen und mehrere aufeinanderfolgende Schrägstriche durch einen einzelnen Schrägstrich zu ersetzen. Wenn der Eintrag vom Typ `:hardlink` ist, wird der Zielpfad ebenfalls auf die gleiche Weise normalisiert, damit er mit dem Pfad des Ziel-Eintrags übereinstimmt; das Größenfeld wird auf die Größe des Zielpfads gesetzt (der bereits gesehen worden sein muss).

Wenn das `portable`-Flag wahr ist, werden die Pfadnamen auf Gültigkeit unter Windows überprüft, was sicherstellt, dass sie keine illegalen Zeichen enthalten oder Namen haben, die reserviert sind. Siehe https://stackoverflow.com/a/31976060/659248 für Details.
