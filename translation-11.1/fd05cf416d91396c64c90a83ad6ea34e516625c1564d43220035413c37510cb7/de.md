```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

Listet die Inhalte eines Tar-Archivs ("tarball"), das sich unter dem Pfad `tarball` befindet. Wenn `tarball` ein IO-Handle ist, werden die Tar-Inhalte aus diesem Stream gelesen. Gibt einen Vektor von `Header`-Strukturen zurück. Siehe [`Header`](@ref) für Details.

Wenn ein `callback` bereitgestellt wird, wird anstelle der Rückgabe eines Vektors von Headern der Callback für jeden `Header` aufgerufen. Dies kann nützlich sein, wenn die Anzahl der Elemente im Tarball groß ist oder wenn Sie Elemente vor einem Fehler im Tarball untersuchen möchten. Wenn die `callback`-Funktion ein zweites Argument vom Typ `Vector{UInt8}` oder `Vector{Pair{Symbol, String}}` akzeptieren kann, wird sie mit einer Darstellung der rohen Headerdaten entweder als einzelner Byte-Vektor oder als Vektor von Paaren, die Feldnamen den rohen Daten für dieses Feld zuordnen, aufgerufen (wenn diese Felder zusammengefügt werden, ergibt das die rohen Daten des Headers).

Standardmäßig wird `list` einen Fehler ausgeben, wenn es auf Inhalte des Tarballs stößt, die die `extract`-Funktion nicht extrahieren würde. Mit `strict=false` werden diese Überprüfungen übersprungen und alle Inhalte der Tar-Datei aufgelistet, unabhängig davon, ob `extract` sie extrahieren würde oder nicht. Seien Sie vorsichtig, dass bösartige Tarballs allerlei raffinierte und unerwartete Dinge tun können, um Sie zu versuchen, etwas Schlechtes zu tun.

Wenn das Argument `tarball` eine Skelettdatei ist (siehe `extract` und `create`), wird `list` dies anhand des Dateikopfes erkennen und die Header der Skelettdatei entsprechend auflisten oder iterieren.
