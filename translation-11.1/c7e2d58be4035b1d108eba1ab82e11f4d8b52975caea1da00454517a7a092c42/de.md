```
read(s::IOStream, nb::Integer; all=true)
```

Liest höchstens `nb` Bytes von `s` und gibt einen `Vector{UInt8}` der gelesenen Bytes zurück.

Wenn `all` `true` ist (der Standardwert), blockiert diese Funktion wiederholt, um alle angeforderten Bytes zu lesen, bis ein Fehler oder das Ende der Datei auftritt. Wenn `all` `false` ist, wird höchstens ein `read`-Aufruf durchgeführt, und die Menge der zurückgegebenen Daten ist geräteabhängig. Beachten Sie, dass nicht alle Streamtypen die `all`-Option unterstützen.
