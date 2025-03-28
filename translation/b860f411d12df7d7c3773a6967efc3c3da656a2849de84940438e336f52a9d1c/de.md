```
readdlm(source; options...)
```

Die Spalten werden als durch ein oder mehrere Leerzeichen getrennt angenommen. Das Zeilenende wird als `\n` betrachtet. Wenn alle Daten numerisch sind, wird das Ergebnis ein numerisches Array sein. Wenn einige Elemente nicht als Zahlen geparst werden können, wird ein heterogenes Array aus Zahlen und Strings zurückgegeben.

# Beispiele

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end;

julia> readdlm("delim_file.txt")
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```
