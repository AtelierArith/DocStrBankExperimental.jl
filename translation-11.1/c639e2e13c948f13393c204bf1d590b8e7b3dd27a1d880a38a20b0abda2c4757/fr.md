```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

Lit une chaîne à partir d'un `flux` I/O ou d'un fichier, jusqu'au délimiteur donné. Le délimiteur peut être un `UInt8`, `AbstractChar`, une chaîne ou un vecteur. L'argument clé `keep` contrôle si le délimiteur est inclus dans le résultat. Le texte est supposé être encodé en UTF-8.

Retourne une `String` si `delim` est un `AbstractChar` ou une chaîne, sinon retourne un `Vector{typeof(delim)}`. Voir aussi [`copyuntil`](@ref) pour écrire à la place dans un autre flux (qui peut être un [`IOBuffer`](@ref) préalloué).

# Exemples

```jldoctest
julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\nElle a de nombreux membres.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang est une organisation GitHub."

julia> rm("my_file.txt")
```
