```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

Lese einen String aus einem I/O `stream` oder einer Datei bis zum angegebenen Trennzeichen. Das Trennzeichen kann ein `UInt8`, `AbstractChar`, String oder Vektor sein. Das Schlüsselwort-Argument `keep` steuert, ob das Trennzeichen im Ergebnis enthalten ist. Der Text wird als in UTF-8 kodiert angenommen.

Gibt einen `String` zurück, wenn `delim` ein `AbstractChar` oder ein String ist, andernfalls wird ein `Vector{typeof(delim)}` zurückgegeben. Siehe auch [`copyuntil`](@ref), um stattdessen in-place in einen anderen Stream zu schreiben (der ein vorab zugewiesenes [`IOBuffer`](@ref) sein kann).

# Beispiele

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang ist eine GitHub-Organisation."

julia> rm("my_file.txt")
```
