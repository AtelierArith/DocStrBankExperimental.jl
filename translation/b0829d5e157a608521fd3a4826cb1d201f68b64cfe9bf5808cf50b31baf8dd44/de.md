```
closewrite(stream)
```

Fährt die Schreibhälfte eines voll-duplex I/O-Streams herunter. Führt zuerst einen [`flush`](@ref) durch. Benachrichtigt das andere Ende, dass keine weiteren Daten in die zugrunde liegende Datei geschrieben werden. Dies wird nicht von allen IO-Typen unterstützt.

Wenn implementiert, bewirkt `closewrite`, dass nachfolgende `read`- oder `eof`-Aufrufe, die blockieren würden, stattdessen EOF auslösen oder true zurückgeben. Wenn der Stream bereits geschlossen ist, ist dies idempotent.

# Beispiele

```jldoctest
julia> io = Base.BufferStream(); # dies blockiert niemals, sodass wir im selben Task lesen und schreiben können

julia> write(io, "request");

julia> # der Aufruf von `read(io)` hier würde für immer blockieren

julia> closewrite(io);

julia> read(io, String)
"request"
```
