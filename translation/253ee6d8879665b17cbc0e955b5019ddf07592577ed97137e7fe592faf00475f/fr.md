```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

Lit tous les lignes d'un flux I/O ou d'un fichier sous forme de vecteur de chaînes. Le comportement est équivalent à la sauvegarde du résultat de la lecture de [`readline`](@ref) de manière répétée avec les mêmes arguments et à la sauvegarde des lignes résultantes sous forme de vecteur de chaînes. Voir aussi [`eachline`](@ref) pour itérer sur les lignes sans les lire toutes en une seule fois.

# Exemples

```jldoctest
julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\nElle a de nombreux membres.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang est une organisation GitHub."
 "Elle a de nombreux membres."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang est une organisation GitHub.\n"
 "Elle a de nombreux membres.\n"

julia> rm("my_file.txt")
```
