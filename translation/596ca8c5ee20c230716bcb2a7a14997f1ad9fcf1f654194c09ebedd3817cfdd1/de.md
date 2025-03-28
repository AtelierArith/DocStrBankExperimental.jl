```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

Lese höchstens `nb` Bytes aus `stream` in `b` und gebe die Anzahl der gelesenen Bytes zurück. Die Größe von `b` wird bei Bedarf erhöht (d.h. wenn `nb` größer als `length(b)` ist und genügend Bytes gelesen werden konnten), aber sie wird niemals verringert.
