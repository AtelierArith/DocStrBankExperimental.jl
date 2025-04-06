```
remote_do(f, id::Integer, args...; kwargs...) -> nothing
```

Führt `f` asynchron auf dem Worker `id` aus. Im Gegensatz zu [`remotecall`](@ref) wird das Ergebnis der Berechnung nicht gespeichert, noch gibt es eine Möglichkeit, auf dessen Abschluss zu warten.

Ein erfolgreicher Aufruf zeigt an, dass die Anfrage zur Ausführung auf dem Remote-Knoten akzeptiert wurde.

Während aufeinanderfolgende `remotecall`s an denselben Worker in der Reihenfolge, in der sie aufgerufen werden, serialisiert werden, ist die Reihenfolge der Ausführungen auf dem Remote-Worker unbestimmt. Zum Beispiel wird `remote_do(f1, 2); remotecall(f2, 2); remote_do(f3, 2)` den Aufruf von `f1` serialisieren, gefolgt von `f2` und `f3` in dieser Reihenfolge. Es ist jedoch nicht garantiert, dass `f1` vor `f3` auf Worker 2 ausgeführt wird.

Alle Ausnahmen, die von `f` ausgelöst werden, werden auf [`stderr`](@ref) des Remote-Workers ausgegeben.

Schlüsselwortargumente, falls vorhanden, werden an `f` weitergegeben.
