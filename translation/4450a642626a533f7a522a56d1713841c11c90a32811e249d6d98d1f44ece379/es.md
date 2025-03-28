```
read(s::IO, nb=typemax(Int))
```

Lee como máximo `nb` bytes de `s`, devolviendo un `Vector{UInt8}` de los bytes leídos.
