```
include_dependency(path::AbstractString; track_content::Bool=true)
```

In einem Modul erklären Sie, dass die Datei, das Verzeichnis oder der symbolische Link, der durch `path` (relativ oder absolut) angegeben ist, eine Abhängigkeit für die Vorcompilierung ist; das heißt, wenn `track_content=true` ist, muss das Modul neu kompiliert werden, wenn sich der Inhalt von `path` ändert (wenn `path` ein Verzeichnis ist, entspricht der Inhalt `join(readdir(path))`). Wenn `track_content=false` ist, wird die Neukompilierung ausgelöst, wenn sich die Änderungszeit `mtime` von `path` ändert.

Dies ist nur erforderlich, wenn Ihr Modul von einem Pfad abhängt, der nicht über [`include`](@ref) verwendet wird. Es hat keine Auswirkungen außerhalb der Kompilierung.

!!! compat "Julia 1.11"
    Das Schlüsselwort-Argument `track_content` erfordert mindestens Julia 1.11. Ein Fehler wird jetzt ausgelöst, wenn `path` nicht lesbar ist.

