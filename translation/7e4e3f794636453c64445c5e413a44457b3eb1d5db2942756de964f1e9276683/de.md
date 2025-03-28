```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

Erstellt einen In-Memory-I/O-Stream, der optional auf einem bereits vorhandenen Array arbeiten kann.

Es können optionale Schlüsselwortargumente übergeben werden:

  * `read`, `write`, `append`: beschränkt die Operationen auf den Puffer; siehe `open` für Details.
  * `truncate`: kürzt die Puffergröße auf null Länge.
  * `maxsize`: gibt eine Größe an, über die der Puffer nicht vergrößert werden darf.
  * `sizehint`: schlägt eine Kapazität des Puffers vor (`data` muss `sizehint!(data, size)` implementieren).

Wenn `data` nicht angegeben ist, ist der Puffer standardmäßig sowohl lesbar als auch schreibbar.

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang ist eine GitHub-Organisation.", " Es hat viele Mitglieder.")
56

julia> String(take!(io))
"JuliaLang ist eine GitHub-Organisation. Es hat viele Mitglieder."

julia> io = IOBuffer(b"JuliaLang ist eine GitHub-Organisation.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang ist eine GitHub-Organisation."

julia> write(io, "Das ist nicht schreibbar.")
ERROR: ArgumentError: ensureroom failed, IOBuffer ist nicht schreibbar

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang ist eine GitHub-Organisation.")
34

julia> String(take!(io))
"JuliaLang ist eine GitHub-Organisation"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
