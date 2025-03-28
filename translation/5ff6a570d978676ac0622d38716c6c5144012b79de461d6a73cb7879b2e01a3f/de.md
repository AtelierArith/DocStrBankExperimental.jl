```
RemoteChannel(pid::Integer=myid())
```

Erstellt eine Referenz zu einem `Channel{Any}(1)` im Prozess `pid`. Der Standardwert für `pid` ist der aktuelle Prozess.

```
RemoteChannel(f::Function, pid::Integer=myid())
```

Erstellt Referenzen zu Remote-Kanälen einer bestimmten Größe und Art. `f` ist eine Funktion, die bei Ausführung auf `pid` eine Implementierung eines `AbstractChannel` zurückgeben muss.

Zum Beispiel wird `RemoteChannel(()->Channel{Int}(10), pid)` eine Referenz zu einem Kanal vom Typ `Int` und der Größe 10 auf `pid` zurückgeben.

Der Standardwert für `pid` ist der aktuelle Prozess.
