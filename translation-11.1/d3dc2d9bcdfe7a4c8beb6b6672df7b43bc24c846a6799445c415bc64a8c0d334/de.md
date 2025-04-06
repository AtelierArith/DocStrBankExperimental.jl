```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

Liest höchstens `nb` Bytes aus `stream` in `b` und gibt die Anzahl der gelesenen Bytes zurück. Die Größe von `b` wird bei Bedarf erhöht (d.h. wenn `nb` größer als `length(b)` ist und genügend Bytes gelesen werden konnten), aber sie wird niemals verringert.

Wenn `all` `true` ist (der Standardwert), blockiert diese Funktion wiederholt, um alle angeforderten Bytes zu lesen, bis ein Fehler oder das Ende der Datei auftritt. Wenn `all` `false` ist, wird höchstens ein `read`-Aufruf durchgeführt, und die Menge der zurückgegebenen Daten ist geräteabhängig. Beachten Sie, dass nicht alle Streamtypen die `all`-Option unterstützen.
