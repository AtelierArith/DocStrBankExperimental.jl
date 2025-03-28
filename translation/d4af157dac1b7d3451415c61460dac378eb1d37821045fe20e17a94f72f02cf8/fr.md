```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)

Copie une chaîne d'un flux I/O `stream` ou d'un fichier, jusqu'au délimiteur donné, vers le flux `out`, en retournant `out`. Le délimiteur peut être un `UInt8`, `AbstractChar`, une chaîne ou un vecteur. L'argument clé `keep` contrôle si le délimiteur est inclus dans le résultat. Le texte est supposé être encodé en UTF-8.

Semblable à [`readuntil`](@ref), qui retourne une `String`; en revanche, `copyuntil` écrit directement dans `out`, sans allouer de chaîne. (Cela peut être utilisé, par exemple, pour lire des données dans un [`IOBuffer`](@ref) pré-alloué.)

# Exemples

```

jldoctest julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L'))) "Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true))) "JuliaLang is a GitHub organization."

julia> rm("my_file.txt") ```
