```
readdlm(source, delim::AbstractChar, T::Type, eol::AbstractChar; header=false, skipstart=0, skipblanks=true, use_mmap, quotes=true, dims, comments=false, comment_char='#')
```

Lire une matrice à partir de la source où chaque ligne (séparée par `eol`) donne une ligne, avec des éléments séparés par le délimiteur donné. La source peut être un fichier texte, un flux ou un tableau d'octets. Des fichiers mappés en mémoire peuvent être utilisés en passant la représentation du tableau d'octets du segment mappé comme source.

Si `T` est un type numérique, le résultat est un tableau de ce type, avec tout élément non numérique comme `NaN` pour les types à virgule flottante, ou zéro. D'autres valeurs utiles de `T` incluent `String`, `AbstractString`, et `Any`.

Si `header` est `true`, la première ligne de données sera lue comme en-tête et le tuple `(data_cells, header_cells)` est retourné au lieu de seulement `data_cells`.

Spécifier `skipstart` ignorera le nombre correspondant de lignes initiales de l'entrée.

Si `skipblanks` est `true`, les lignes vides dans l'entrée seront ignorées.

Si `use_mmap` est `true`, le fichier spécifié par `source` est mappé en mémoire pour des gains de vitesse potentiels si le fichier est volumineux. La valeur par défaut est `false`. Sur un système de fichiers Windows, `use_mmap` ne doit pas être défini sur `true` à moins que le fichier ne soit lu qu'une seule fois et ne soit également pas écrit. Certains cas particuliers existent où un OS est de type Unix mais le système de fichiers est de type Windows.

Si `quotes` est `true`, les colonnes entourées de caractères de guillemet double (") peuvent contenir des nouvelles lignes et des délimiteurs de colonnes. Les caractères de guillemet double à l'intérieur d'un champ cité doivent être échappés avec un autre guillemet double. Spécifier `dims` comme un tuple des lignes et colonnes attendues (y compris l'en-tête, le cas échéant) peut accélérer la lecture de fichiers volumineux. Si `comments` est `true`, les lignes commençant par `comment_char` et le texte suivant `comment_char` dans n'importe quelle ligne sont ignorés.

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
