```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

Créez un flux d'E/S en mémoire, qui peut éventuellement fonctionner sur un tableau préexistant.

Il peut prendre des arguments de mot-clé optionnels :

  * `read`, `write`, `append` : restreint les opérations au tampon ; voir `open` pour plus de détails.
  * `truncate` : tronque la taille du tampon à une longueur nulle.
  * `maxsize` : spécifie une taille au-delà de laquelle le tampon ne peut pas être agrandi.
  * `sizehint` : suggère une capacité du tampon (`data` doit implémenter `sizehint!(data, size)`).

Lorsque `data` n'est pas donné, le tampon sera à la fois lisible et inscriptible par défaut.

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> io = IOBuffer(b"JuliaLang is a GitHub organization.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang is a GitHub organization."

julia> write(io, "This isn't writable.")
ERROR: ArgumentError: ensureroom failed, IOBuffer is not writeable

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang is a GitHub organization.")
34

julia> String(take!(io))
"JuliaLang is a GitHub organization"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
