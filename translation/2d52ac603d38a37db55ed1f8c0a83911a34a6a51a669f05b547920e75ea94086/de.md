```
eof(stream) -> Bool
```

Testen, ob ein I/O-Stream am Ende der Datei ist. Wenn der Stream noch nicht erschöpft ist, wird diese Funktion blockieren, um auf weitere Daten zu warten, falls erforderlich, und dann `false` zurückgeben. Daher ist es immer sicher, ein Byte zu lesen, nachdem `eof` `false` zurückgegeben hat. `eof` gibt `false` zurück, solange gepufferte Daten noch verfügbar sind, selbst wenn das entfernte Ende einer Verbindung geschlossen ist.

# Beispiele

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```
