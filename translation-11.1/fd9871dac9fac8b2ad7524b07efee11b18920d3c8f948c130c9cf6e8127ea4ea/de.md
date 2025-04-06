```
Base64DecodePipe(istream)
```

Gibt einen neuen schreibgeschützten I/O-Stream zurück, der die base64-kodierten Daten decodiert, die von `istream` gelesen werden.

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
