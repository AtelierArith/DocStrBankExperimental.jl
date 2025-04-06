```
Base64DecodePipe(istream)
```

Renvoie un nouveau flux d'E/S en lecture seule, qui décode les données encodées en base64 lues à partir de `istream`.

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
