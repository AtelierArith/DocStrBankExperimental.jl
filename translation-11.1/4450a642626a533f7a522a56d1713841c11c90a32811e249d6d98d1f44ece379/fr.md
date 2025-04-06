```
read(s::IO, nb=typemax(Int))
```

Lire au maximum `nb` octets de `s`, renvoyant un `Vector{UInt8}` des octets lus.
