```
Base64DecodePipe(istream)
```

Devuelve un nuevo flujo de E/S de solo lectura, que decodifica datos codificados en base64 leídos de `istream`.

# Ejemplos

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
