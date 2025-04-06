```
FILE(::Ptr)
FILE(::IO)
```

Un `FILE*` de libc, représentant un fichier ouvert.

Il peut être passé comme argument `Ptr{FILE}` à [`ccall`](@ref) et prend également en charge [`seek`](@ref), [`position`](@ref) et [`close`](@ref).

Un `FILE` peut être construit à partir d'un objet `IO` ordinaire, à condition qu'il s'agisse d'un fichier ouvert. Il doit être fermé par la suite.

# Exemples

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # écrire dans le fichier temporaire en utilisant `puts(char*, FILE*)` de libc
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # lire à nouveau le fichier
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
