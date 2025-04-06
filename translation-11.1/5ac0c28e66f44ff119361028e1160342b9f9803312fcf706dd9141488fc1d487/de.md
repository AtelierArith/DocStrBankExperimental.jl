```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')
```

Liest `io` bis zum Ende des Streams/der Datei und zählt die Anzahl der Zeilen. Um eine Datei anzugeben, übergeben Sie den Dateinamen als erstes Argument. EOL-Markierungen, die nicht `'\n'` sind, werden unterstützt, indem sie als zweites Argument übergeben werden. Die letzte nicht-leere Zeile von `io` wird gezählt, auch wenn sie nicht mit dem EOL endet, was der Länge entspricht, die von [`eachline`](@ref) und [`readlines`](@ref) zurückgegeben wird.

Um die Zeilen eines `String` zu zählen, kann `countlines(IOBuffer(str))` verwendet werden.

# Beispiele

```jldoctest
julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.\n");

julia> countlines(io)
1

julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> countlines(io)
1

julia> eof(io) # Zeilen zählen bewegt den Dateizeiger
true

julia> io = IOBuffer("JuliaLang ist eine GitHub-Organisation.");

julia> countlines(io, eol = '.')
1
```

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\n")
36

julia> countlines("my_file.txt")
1

julia> countlines("my_file.txt", eol = 'n')
4

julia> rm("my_file.txt")

```
