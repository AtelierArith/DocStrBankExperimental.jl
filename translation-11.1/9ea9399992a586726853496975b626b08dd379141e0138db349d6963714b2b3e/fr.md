```
writedlm(f, A, delim='\t'; opts)
```

Écrit `A` (un vecteur, une matrice ou une collection itérable de lignes itérables) en tant que texte dans `f` (soit une chaîne de caractères de nom de fichier, soit un flux `IO`) en utilisant le délimiteur donné `delim` (qui par défaut est une tabulation, mais peut être n'importe quel objet Julia imprimable, typiquement un `Char` ou un `AbstractString`).

Par exemple, deux vecteurs `x` et `y` de la même longueur peuvent être écrits comme deux colonnes de texte délimité par des tabulations dans `f` soit par `writedlm(f, [x y])` soit par `writedlm(f, zip(x, y))`.

# Exemples

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
