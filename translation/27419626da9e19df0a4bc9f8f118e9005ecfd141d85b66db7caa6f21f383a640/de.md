```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

Kopiere die Datei, den Link oder das Verzeichnis von `src` nach `dst`. `force=true` entfernt zuerst ein vorhandenes `dst`.

Wenn `follow_symlinks=false` und `src` ein symbolischer Link ist, wird `dst` als symbolischer Link erstellt. Wenn `follow_symlinks=true` und `src` ein symbolischer Link ist, wird `dst` eine Kopie der Datei oder des Verzeichnisses, auf das `src` verweist. Rückgabe von `dst`.

!!! note
    Die Funktion `cp` unterscheidet sich vom Befehl `cp`. Die Funktion `cp` geht immer davon aus, dass `dst` eine Datei ist, während der Befehl je nach dem, ob `dst` ein Verzeichnis oder eine Datei ist, unterschiedliche Dinge tut. Die Verwendung von `force=true`, wenn `dst` ein Verzeichnis ist, führt zum Verlust aller Inhalte im `dst`-Verzeichnis, und `dst` wird zu einer Datei, die die Inhalte von `src` enthält.

