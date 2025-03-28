```
truncate(file, n)
```

Redimensionne le fichier ou le tampon donné par le premier argument à exactement `n` octets, remplissant l'espace précédemment non alloué avec '\0' si le fichier ou le tampon est agrandi.

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.")
35

julia> truncate(io, 15)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=15, maxsize=Inf, ptr=16, mark=-1)

julia> String(take!(io))
"JuliaLang is a "

julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.");

julia> truncate(io, 40);

julia> String(take!(io))
"JuliaLang is a GitHub organization.\0\0\0\0\0"
```
