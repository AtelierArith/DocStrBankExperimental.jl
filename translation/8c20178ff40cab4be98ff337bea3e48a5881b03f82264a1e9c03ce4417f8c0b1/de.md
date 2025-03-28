```
withenv(f, kv::Pair...)
```

Führen Sie `f` in einer Umgebung aus, die vorübergehend modifiziert (nicht ersetzt wie in `setenv`) wird durch null oder mehr `"var"=>val` Argumente `kv`. `withenv` wird allgemein über die Syntax `withenv(kv...) do ... end` verwendet. Ein Wert von `nothing` kann verwendet werden, um eine Umgebungsvariable vorübergehend zu deaktivieren (wenn sie gesetzt ist). Wenn `withenv` zurückkehrt, wurde die ursprüngliche Umgebung wiederhergestellt.

!!! warning
    Das Ändern der Umgebung ist nicht threadsicher. Für das Ausführen externer Befehle mit einer anderen Umgebung als dem übergeordneten Prozess wird empfohlen, [`addenv`](@ref) anstelle von `withenv` zu verwenden.

