```
replace([io::IO], s::AbstractString, pat=>r, [pat2=>r2, ...]; [count::Integer])
```

Recherchez le motif donné `pat` dans `s`, et remplacez chaque occurrence par `r`. Si `count` est fourni, remplacez au maximum `count` occurrences. `pat` peut être un seul caractère, un vecteur ou un ensemble de caractères, une chaîne de caractères, ou une expression régulière. Si `r` est une fonction, chaque occurrence est remplacée par `r(s)` où `s` est la sous-chaîne correspondante (lorsque `pat` est un `AbstractPattern` ou `AbstractString`) ou un caractère (lorsque `pat` est un `AbstractChar` ou une collection de `AbstractChar`). Si `pat` est une expression régulière et `r` est une [`SubstitutionString`](@ref), alors les références de groupe de capture dans `r` sont remplacées par le texte correspondant. Pour supprimer les instances de `pat` de `string`, définissez `r` sur la chaîne vide (`""`).

La valeur de retour est une nouvelle chaîne après les remplacements. Si l'argument `io::IO` est fourni, la chaîne transformée est plutôt écrite dans `io` (retournant `io`). (Par exemple, cela peut être utilisé en conjonction avec un [`IOBuffer`](@ref) pour réutiliser un tableau de tampon pré-alloué sur place.)

Plusieurs motifs peuvent être spécifiés, et ils seront appliqués de gauche à droite simultanément, donc un seul motif sera appliqué à un caractère, et les motifs ne seront appliqués qu'au texte d'entrée, pas aux remplacements.

!!! compat "Julia 1.7"
    Le support pour plusieurs motifs nécessite la version 1.7.


!!! compat "Julia 1.10"
    L'argument `io::IO` nécessite la version 1.10.


# Exemples

```jldoctest
julia> replace("Python is a programming language.", "Python" => "Julia")
"Julia is a programming language."

julia> replace("The quick foxes run quickly.", "quick" => "slow", count=1)
"The slow foxes run quickly."

julia> replace("The quick foxes run quickly.", "quick" => "", count=1)
"The  foxes run quickly."

julia> replace("The quick foxes run quickly.", r"fox(es)?" => s"bus\1")
"The quick buses run quickly."

julia> replace("abcabc", "a" => "b", "b" => "c", r".+" => "a")
"bca"
```
