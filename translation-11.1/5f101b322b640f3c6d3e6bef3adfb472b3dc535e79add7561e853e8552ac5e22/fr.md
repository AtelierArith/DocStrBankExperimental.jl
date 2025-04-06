```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

Créez un objet itérable `EachLine` qui renverra chaque ligne d'un flux I/O ou d'un fichier. L'itération appelle [`readline`](@ref) sur l'argument de flux de manière répétée avec `keep` passé, déterminant si les caractères de fin de ligne sont conservés. Lorsqu'il est appelé avec un nom de fichier, le fichier est ouvert une fois au début de l'itération et fermé à la fin. Si l'itération est interrompue, le fichier sera fermé lorsque l'objet `EachLine` sera collecté par le ramasse-miettes.

Pour itérer sur chaque ligne d'une `String`, `eachline(IOBuffer(str))` peut être utilisé.

[`Iterators.reverse`](@ref) peut être utilisé sur un objet `EachLine` pour lire les lignes dans l'ordre inverse (pour les fichiers, les tampons et d'autres flux I/O prenant en charge [`seek`](@ref)), et [`first`](@ref) ou [`last`](@ref) peuvent être utilisés pour extraire respectivement les lignes initiales ou finales.

# Exemples

```jldoctest
julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\n Elle a de nombreux membres.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang est une organisation GitHub. Elle a de nombreux membres.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    Julia 1.8 est requis pour utiliser `Iterators.reverse` ou `last` avec les itérateurs `eachline`.

