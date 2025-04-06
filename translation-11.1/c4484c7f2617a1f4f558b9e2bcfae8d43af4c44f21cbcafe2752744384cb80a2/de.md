```
truncate(file, n)
```

Ändert die Größe der Datei oder des Puffers, die durch das erste Argument angegeben ist, auf genau `n` Bytes und füllt zuvor nicht zugewiesenen Speicher mit '\0', wenn die Datei oder der Puffer vergrößert wird.

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang ist eine GitHub-Organisation.")
35

julia> truncate(io, 15)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=15, maxsize=Inf, ptr=16, mark=-1)

julia> String(take!(io))
"JuliaLang ist eine "

julia> io = IOBuffer();

julia> write(io, "JuliaLang ist eine GitHub-Organisation.");

julia> truncate(io, 40);

julia> String(take!(io))
"JuliaLang ist eine GitHub-Organisation.\0\0\0\0\0"
```
