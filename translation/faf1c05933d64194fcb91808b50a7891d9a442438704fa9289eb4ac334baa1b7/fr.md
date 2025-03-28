```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

Lit une seule ligne de texte à partir du flux d'E/S ou du fichier donné (par défaut `stdin`). Lors de la lecture à partir d'un fichier, le texte est supposé être encodé en UTF-8. Les lignes dans l'entrée se terminent par `'\n'` ou `"\r\n"` ou la fin d'un flux d'entrée. Lorsque `keep` est faux (comme c'est le cas par défaut), ces caractères de nouvelle ligne finaux sont supprimés de la ligne avant qu'elle ne soit renvoyée. Lorsque `keep` est vrai, ils sont renvoyés comme partie de la ligne.

Renvoie un `String`.   Voir aussi [`copyline`](@ref) pour écrire à la place en place dans un autre flux (qui peut être un [`IOBuffer`](@ref) préalloué).

Voir aussi [`readuntil`](@ref) pour lire jusqu'à des délimiteurs plus généraux.

# Exemples

```jldoctest
julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\nElle a de nombreux membres.\n");

julia> readline("my_file.txt")
"JuliaLang est une organisation GitHub."

julia> readline("my_file.txt", keep=true)
"JuliaLang est une organisation GitHub.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Entrez votre nom : ")
Entrez votre nom :

julia> your_name = readline()
Logan
"Logan"
```
