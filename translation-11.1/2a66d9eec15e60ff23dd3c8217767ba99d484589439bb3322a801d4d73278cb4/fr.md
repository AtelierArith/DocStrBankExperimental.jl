```
graphemes(s::AbstractString, m:n) -> SubString
```

Renvoie un [`SubString`](@ref) de `s` consistant en les graphèmes `m`-ième à `n`-ième de la chaîne `s`, où le deuxième argument `m:n` est un [`AbstractUnitRange`](@ref) de type entier.

De manière générale, cela correspond aux "caractères" perçus par l'utilisateur de `m:n` dans la chaîne. Par exemple :

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (catégorie Ll: Lettre, minuscule)
 'o': ASCII/Unicode U+006F (catégorie Ll: Lettre, minuscule)
 's': ASCII/Unicode U+0073 (catégorie Ll: Lettre, minuscule)
 'e': ASCII/Unicode U+0065 (catégorie Ll: Lettre, minuscule)
 '́': Unicode U+0301 (catégorie Mn: Marque, non espacée)
```

Cela consiste en les 3ème à *7ème* points de code ([`Char`](@ref)s) dans `"exposé"`, car le graphème `"é"` est en réalité *deux* points de code Unicode (un `'e'` suivi d'un caractère combinant accent aigu U+0301).

Parce que trouver les limites des graphèmes nécessite une itération sur le contenu de la chaîne, la fonction `graphemes(s, m:n)` nécessite un temps proportionnel à la longueur de la chaîne (nombre de points de code) avant la fin de la sous-chaîne.

!!! compat "Julia 1.9"
    L'argument `m:n` de `graphemes` nécessite Julia 1.9.

