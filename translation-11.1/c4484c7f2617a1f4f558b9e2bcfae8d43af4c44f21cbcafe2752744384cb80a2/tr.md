```
truncate(file, n)
```

Verilen dosyayı veya tamponu ilk argüman olarak `n` bayta tam olarak yeniden boyutlandırır, eğer dosya veya tampon büyütülürse daha önce tahsis edilmemiş alanı '\0' ile doldurur.

# Örnekler

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
