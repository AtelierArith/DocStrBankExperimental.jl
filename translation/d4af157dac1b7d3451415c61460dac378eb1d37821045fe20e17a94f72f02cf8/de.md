```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)

Kopiert einen String aus einem I/O `stream` oder einer Datei bis zum angegebenen Trennzeichen in den `out`-Stream und gibt `out` zurück. Das Trennzeichen kann ein `UInt8`, `AbstractChar`, String oder Vektor sein. Das Schlüsselwort-Argument `keep` steuert, ob das Trennzeichen im Ergebnis enthalten ist. Der Text wird als in UTF-8 kodiert angenommen.

Ähnlich wie [`readuntil`](@ref), das einen `String` zurückgibt; im Gegensatz dazu schreibt `copyuntil` direkt in `out`, ohne einen String zuzuweisen. (Dies kann beispielsweise verwendet werden, um Daten in einen vorab zugewiesenen [`IOBuffer`](@ref) zu lesen.)

# Beispiele

```

jldoctest julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L'))) "Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true))) "JuliaLang ist eine GitHub-Organisation."

julia> rm("my_file.txt") ```
