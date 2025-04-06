```
Base64DecodePipe(istream)
```

Yeni bir yalnızca okuma I/O akışı döndürür; bu akış, `istream`'den okunan base64 kodlu verileri çözer.

# Örnekler

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
