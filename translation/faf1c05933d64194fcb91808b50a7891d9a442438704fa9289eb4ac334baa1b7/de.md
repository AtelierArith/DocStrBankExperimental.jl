```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

Liest eine einzelne Zeile Text aus dem angegebenen I/O-Stream oder der Datei (standardmäßig `stdin`). Beim Lesen aus einer Datei wird angenommen, dass der Text in UTF-8 kodiert ist. Zeilen im Eingabestrom enden mit `'\n'` oder `"\r\n"` oder dem Ende eines Eingabestroms. Wenn `keep` false ist (wie standardmäßig), werden diese nachfolgenden Zeilenumbrüche von der Zeile entfernt, bevor sie zurückgegeben wird. Wenn `keep` true ist, werden sie als Teil der Zeile zurückgegeben.

Gibt einen `String` zurück. Siehe auch [`copyline`](@ref), um stattdessen in-place in einen anderen Stream zu schreiben (der ein vorab zugewiesenes [`IOBuffer`](@ref) sein kann).

Siehe auch [`readuntil`](@ref) zum Lesen bis zu allgemeineren Trennzeichen.

# Beispiele

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> readline("my_file.txt")
"JuliaLang ist eine GitHub-Organisation."

julia> readline("my_file.txt", keep=true)
"JuliaLang ist eine GitHub-Organisation.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Geben Sie Ihren Namen ein: ")
Geben Sie Ihren Namen ein:

julia> your_name = readline()
Logan
"Logan"
```
