```
unsafe_read(io::IO, ref, nbytes::UInt)
```

Copia `nbytes` del objeto de flujo `IO` en `ref` (convertido a un puntero).

Se recomienda que los subtipos `T<:IO` sobrescriban la siguiente firma de método para proporcionar implementaciones más eficientes: `unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
