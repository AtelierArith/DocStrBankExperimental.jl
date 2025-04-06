```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

Mettez en majuscule le premier caractère de chaque mot dans `s` ; si `strict` est vrai, chaque autre caractère est converti en minuscule, sinon ils restent inchangés. Par défaut, tous les caractères non alphabétiques commençant un nouveau graphe sont considérés comme des séparateurs de mots ; un prédicat peut être passé en tant que mot-clé `wordsep` pour déterminer quels caractères doivent être considérés comme des séparateurs de mots. Voir aussi [`uppercasefirst`](@ref) pour mettre en majuscule uniquement le premier caractère de `s`.

Voir aussi [`uppercase`](@ref), [`lowercase`](@ref), [`uppercasefirst`](@ref).

# Exemples

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```
