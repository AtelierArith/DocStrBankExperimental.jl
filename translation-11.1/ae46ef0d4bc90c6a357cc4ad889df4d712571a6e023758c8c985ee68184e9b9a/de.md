```
macro artifact_str(name)
```

Gibt den Pfad auf der Festplatte zu einem Artefakt zurück. Sucht automatisch das Artefakt anhand des Namens in der `(Julia)Artifacts.toml`-Datei des Projekts. Wirft einen Fehler, wenn das angeforderte Artefakt nicht vorhanden ist. Wenn es im REPL ausgeführt wird, sucht es nach der toml-Datei, beginnend im aktuellen Verzeichnis, siehe `find_artifacts_toml()` für mehr.

Wenn das Artefakt als "lazy" markiert ist und das Paket `using LazyArtifacts` definiert hat, wird das Artefakt bei Bedarf mit `Pkg` heruntergeladen, wenn dieses Makro zum ersten Mal versucht, den Pfad zu berechnen. Die Dateien werden dann lokal installiert gelassen für später.

Wenn `name` einen Vorwärts- oder Rückwärtsschrägstrich enthält, werden alle Elemente nach dem ersten Schrägstrich als Pfadnamen betrachtet, die in das Artefakt indizieren, was eine einfache Einzeiler-Zugriffsweise auf eine einzelne Datei/ein Verzeichnis innerhalb eines Artefakts ermöglicht. Beispiel:

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! compat "Julia 1.3"
    Dieses Makro erfordert mindestens Julia 1.3.


!!! compat "Julia 1.6"
    Das Slash-Indexing erfordert mindestens Julia 1.6.

