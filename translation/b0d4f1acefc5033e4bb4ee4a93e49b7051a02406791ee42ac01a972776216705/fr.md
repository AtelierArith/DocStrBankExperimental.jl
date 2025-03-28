```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)

Copie une seule ligne de texte d'un `flux` I/O ou d'un fichier vers le flux `out`, retournant `out`.

Lors de la lecture d'un fichier, le texte est supposé être encodé en UTF-8. Les lignes dans l'entrée se terminent par `'\n'` ou `"\r\n"` ou la fin d'un flux d'entrée. Lorsque `keep` est faux (comme c'est le cas par défaut), ces caractères de nouvelle ligne finaux sont supprimés de la ligne avant qu'elle ne soit retournée. Lorsque `keep` est vrai, ils sont retournés comme partie de la ligne.

Semblable à [`readline`](@ref), qui retourne une `String`; en revanche, `copyline` écrit directement dans `out`, sans allouer de chaîne. (Cela peut être utilisé, par exemple, pour lire des données dans un [`IOBuffer`](@ref) pré-alloué.)

Voir aussi [`copyuntil`](@ref) pour lire jusqu'à des délimiteurs plus généraux.

# Exemples

```

jldoctest julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\nElle a de nombreux membres.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt"))) "JuliaLang est une organisation GitHub."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true))) "JuliaLang est une organisation GitHub.\n"

julia> rm("my_file.txt") ```
