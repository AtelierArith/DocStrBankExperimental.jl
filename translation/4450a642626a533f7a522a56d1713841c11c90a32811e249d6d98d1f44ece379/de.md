```
read(s::IO, nb=typemax(Int))
```

Lese höchstens `nb` Bytes von `s` und gebe einen `Vector{UInt8}` der gelesenen Bytes zurück.
