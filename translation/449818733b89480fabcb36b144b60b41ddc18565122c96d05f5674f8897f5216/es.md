```
unsafe_write(io::IO, ref, nbytes::UInt)
```

Copia `nbytes` de `ref` (convertido a un puntero) en el objeto `IO`.

Se recomienda que los subtipos `T<:IO` sobrescriban la siguiente firma de método para proporcionar implementaciones más eficientes: `unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
