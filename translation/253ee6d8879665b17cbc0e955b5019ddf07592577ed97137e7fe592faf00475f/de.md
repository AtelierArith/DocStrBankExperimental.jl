```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

Liest alle Zeilen eines I/O-Streams oder einer Datei als Vektor von Strings. Das Verhalten entspricht dem Speichern des Ergebnisses des wiederholten Lesens von [`readline`](@ref) mit denselben Argumenten und dem Speichern der resultierenden Zeilen als Vektor von Strings. Siehe auch [`eachline`](@ref), um über die Zeilen zu iterieren, ohne sie alle auf einmal zu lesen.

# Beispiele

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang ist eine GitHub-Organisation."
 "Es hat viele Mitglieder."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang ist eine GitHub-Organisation.\n"
 "Es hat viele Mitglieder.\n"

julia> rm("my_file.txt")
```
