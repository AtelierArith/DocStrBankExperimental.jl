```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)

Kopiert eine einzelne Zeile Text von einem I/O `stream` oder einer Datei in den `out`-Stream und gibt `out` zurück.

Beim Lesen aus einer Datei wird angenommen, dass der Text in UTF-8 kodiert ist. Zeilen im Eingangsbereich enden mit `'\n'` oder `"\r\n"` oder dem Ende eines Eingabestreams. Wenn `keep` false ist (wie es standardmäßig der Fall ist), werden diese nachfolgenden Zeilenumbrüche von der Zeile entfernt, bevor sie zurückgegeben wird. Wenn `keep` true ist, werden sie als Teil der Zeile zurückgegeben.

Ähnlich wie [`readline`](@ref), das einen `String` zurückgibt; im Gegensatz dazu schreibt `copyline` direkt in `out`, ohne einen String zuzuweisen. (Dies kann beispielsweise verwendet werden, um Daten in einen vorab zugewiesenen [`IOBuffer`](@ref) zu lesen.)

Siehe auch [`copyuntil`](@ref) zum Lesen bis zu allgemeineren Trennzeichen.

# Beispiele

```

jldoctest julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt"))) "JuliaLang ist eine GitHub-Organisation."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true))) "JuliaLang ist eine GitHub-Organisation.\n"

julia> rm("my_file.txt") ```
