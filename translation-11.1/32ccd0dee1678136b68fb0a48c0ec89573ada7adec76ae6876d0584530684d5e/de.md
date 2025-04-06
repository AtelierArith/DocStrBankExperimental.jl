```
tree_hash([ predicate, ] tarball;
          [ algorithm = "git-sha1", ]
          [ skip_empty = false ]) -> hash::String

    predicate  :: Header --> Bool
    tarball    :: Union{AbstractString, AbstractCmd, IO}
    algorithm  :: AbstractString
    skip_empty :: Bool
```

Berechnen Sie einen Baum-Hashwert für den Dateibaum, den das Tarball enthält. Standardmäßig verwendet dies den Baum-Hashing-Algorithmus von git mit der SHA1-sicheren Hashfunktion (wie aktuelle Versionen von git). Das bedeutet, dass für jedes Tarball, dessen Dateibaum git darstellen kann – d.h. eines mit nur Dateien, Symlinks und nicht leeren Verzeichnissen – der von dieser Funktion berechnete Hashwert derselbe sein wird wie der Hashwert, den git für diesen Dateibaum berechnen würde. Beachten Sie, dass Tarballs Dateibäume mit leeren Verzeichnissen darstellen können, die git nicht speichern kann, und diese Funktion kann Hashes für diese generieren, die standardmäßig (siehe `skip_empty` unten, um dieses Verhalten zu ändern) von dem Hash eines Tarballs abweichen, der diese leeren Verzeichnisse weglässt. Kurz gesagt, die Hashfunktion stimmt mit git bei allen Bäumen überein, die git darstellen kann, erweitert jedoch (auf konsistente Weise) den Bereich der hashbaren Bäume auf andere Bäume, die git nicht darstellen kann.

Wenn eine `predicate`-Funktion übergeben wird, wird sie für jedes `Header`-Objekt aufgerufen, das beim Verarbeiten des `tarball` begegnet, und ein Eintrag wird nur gehasht, wenn `predicate(hdr)` wahr ist. Dies kann verwendet werden, um selektiv nur Teile eines Archivs zu hashen, um Einträge zu überspringen, die dazu führen, dass `extract` einen Fehler auslöst, oder um aufzuzeichnen, was während des Hashing-Prozesses extrahiert wird.

Bevor es an die Prädikatsfunktion übergeben wird, wird das `Header`-Objekt etwas von der rohen Kopfzeile im Tarball modifiziert: Das `path`-Feld wird normalisiert, um `.`-Einträge zu entfernen und mehrere aufeinanderfolgende Schrägstriche durch einen einzelnen Schrägstrich zu ersetzen. Wenn der Eintrag vom Typ `:hardlink` ist, wird der Linkzielpfad auf die gleiche Weise normalisiert, damit er mit dem Pfad des Ziel-Eintrags übereinstimmt; das Größenfeld wird auf die Größe des Zielpfads gesetzt (der bereits gesehen worden sein muss).

Derzeit unterstützte Werte für `algorithm` sind `git-sha1` (der Standard) und `git-sha256`, das denselben grundlegenden Algorithmus wie `git-sha1` verwendet, aber die SHA1-Hashfunktion durch SHA2-256 ersetzt, die Hashfunktion, zu der git in Zukunft übergehen wird (aufgrund bekannter Angriffe auf SHA1). Die Unterstützung für andere Dateibaum-Hashing-Algorithmen kann in Zukunft hinzugefügt werden.

Die Option `skip_empty` steuert, ob Verzeichnisse im Tarball, die rekursiv keine Dateien oder Symlinks enthalten, im Hash enthalten oder ignoriert werden. Im Allgemeinen, wenn Sie den Inhalt eines Tarballs oder eines Dateibaums hashen, interessieren Sie sich für alle Verzeichnisse, nicht nur für nicht leere, sodass die Einbeziehung dieser in den berechneten Hash der Standard ist. Warum bietet diese Funktion also überhaupt die Option, leere Verzeichnisse zu überspringen? Weil git sich weigert, leere Verzeichnisse zu speichern, und sie ignoriert, wenn Sie versuchen, sie zu einem Repo hinzuzufügen. Wenn Sie also einen Referenzbaum-Hash berechnen, indem Sie Dateien zu einem git-Repo hinzufügen und dann git nach dem Baum-Hash fragen, wird der Hashwert, den Sie erhalten, mit dem Hashwert übereinstimmen, der von `tree_hash` mit `skip_empty=true` berechnet wurde. Mit anderen Worten, diese Option ermöglicht es `tree_hash`, zu emulieren, wie git einen Baum mit leeren Verzeichnissen hashen würde. Wenn Sie jedoch Bäume hashen, die leere Verzeichnisse enthalten können (d.h. nicht aus einem git-Repo stammen), wird empfohlen, diese mit einem Tool (wie diesem) zu hashen, das leere Verzeichnisse nicht ignoriert.
