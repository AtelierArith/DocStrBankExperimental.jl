```
readdlm(source; options...)
```

Les colonnes sont supposées être séparées par un ou plusieurs espaces. Le délimiteur de fin de ligne est considéré comme `\n`. Si toutes les données sont numériques, le résultat sera un tableau numérique. Si certains éléments ne peuvent pas être analysés comme des nombres, un tableau hétérogène de nombres et de chaînes est renvoyé.

# Exemples

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
