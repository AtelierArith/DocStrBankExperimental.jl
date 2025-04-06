```
symlink(target::AbstractString, link::AbstractString; dir_target = false)
```

Erstellt einen symbolischen Link zu `target` mit dem Namen `link`.

Unter Windows müssen symbolische Links ausdrücklich als Verweis auf ein Verzeichnis oder nicht deklariert werden. Wenn `target` bereits existiert, wird standardmäßig der Typ von `link` automatisch erkannt. Wenn `target` jedoch nicht existiert, erstellt diese Funktion standardmäßig einen Dateisymbollink, es sei denn, `dir_target` ist auf `true` gesetzt. Beachten Sie, dass, wenn der Benutzer `dir_target` festlegt, `target` jedoch existiert und eine Datei ist, ein Verzeichnissymbollink weiterhin erstellt wird, das Dereferenzieren des Links jedoch fehlschlägt, genau wie wenn der Benutzer einen Dateisymbollink erstellt (indem er `symlink()` mit `dir_target` auf `false` vor dem Erstellen des Verzeichnisses aufruft) und versucht, ihn auf ein Verzeichnis zu dereferenzieren.

Darüber hinaus gibt es zwei Methoden, um einen Link unter Windows zu erstellen: symbolische Links und Junction-Punkte. Junction-Punkte sind etwas effizienter, unterstützen jedoch keine relativen Pfade. Wenn also ein relativer Verzeichnissymbollink angefordert wird (wie durch `isabspath(target)` angezeigt, das `false` zurückgibt), wird ein Symbollink verwendet, andernfalls wird ein Junction-Punkt verwendet. Die beste Praxis zum Erstellen von Symbollinks unter Windows besteht darin, sie nur zu erstellen, nachdem die Dateien/Verzeichnisse, auf die sie verweisen, bereits erstellt wurden.

Siehe auch: [`hardlink`](@ref).

!!! note
    Diese Funktion löst einen Fehler unter Betriebssystemen aus, die keine weichen symbolischen Links unterstützen, wie z. B. Windows XP.


!!! compat "Julia 1.6"
    Das Schlüsselwortargument `dir_target` wurde in Julia 1.6 hinzugefügt. Davor waren symbolische Links zu nicht vorhandenen Pfaden unter Windows immer Dateisymbollinks, und relative symbolische Links zu Verzeichnissen wurden nicht unterstützt.

