```
writedlm(f, A, delim='\t'; opts)
```

Schreibt `A` (einen Vektor, eine Matrix oder eine durchlaufbare Sammlung von durchlaufbaren Zeilen) als Text in `f` (entweder ein Dateinamen-String oder ein `IO`-Stream) unter Verwendung des angegebenen Trennzeichens `delim` (das standardmäßig Tabulator ist, aber jedes druckbare Julia-Objekt sein kann, typischerweise ein `Char` oder `AbstractString`).

Zum Beispiel können zwei Vektoren `x` und `y` derselben Länge als zwei Spalten von tabulatorgetrenntem Text in `f` geschrieben werden, entweder durch `writedlm(f, [x y])` oder durch `writedlm(f, zip(x, y))`.

# Beispiele

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
