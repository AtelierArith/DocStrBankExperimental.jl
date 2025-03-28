```
MIME
```

Un type représentant un format de données Internet standard. "MIME" signifie "Multipurpose Internet Mail Extensions", car la norme a été initialement utilisée pour décrire des pièces jointes multimédias aux messages électroniques.

Un objet `MIME` peut être passé comme deuxième argument à [`show`](@ref) pour demander une sortie dans ce format.

# Exemples

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```
