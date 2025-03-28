```
FILE(::Ptr)
FILE(::IO)
```

Ein libc `FILE*`, das eine geöffnete Datei darstellt.

Es kann als `Ptr{FILE}`-Argument an [`ccall`](@ref) übergeben werden und unterstützt auch [`seek`](@ref), [`position`](@ref) und [`close`](@ref).

Ein `FILE` kann aus einem gewöhnlichen `IO`-Objekt konstruiert werden, vorausgesetzt, es handelt sich um eine geöffnete Datei. Es muss anschließend geschlossen werden.

# Beispiele

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # in die temporäre Datei schreiben mit `puts(char*, FILE*)` aus libc
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # die Datei erneut lesen
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
