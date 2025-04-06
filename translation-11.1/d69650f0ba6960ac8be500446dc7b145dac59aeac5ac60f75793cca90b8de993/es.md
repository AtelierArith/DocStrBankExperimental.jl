```
read(filename::AbstractString)
```

Lee todo el contenido de un archivo como un `Vector{UInt8}`.

```
read(filename::AbstractString, String)
```

Lee todo el contenido de un archivo como una cadena.

```
read(filename::AbstractString, args...)
```

Abre un archivo y lee su contenido. `args` se pasa a `read`: esto es equivalente a `open(io->read(io, args...), filename)`.
