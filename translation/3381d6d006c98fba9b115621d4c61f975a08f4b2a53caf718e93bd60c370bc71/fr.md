```
reverse(s::AbstractString) -> AbstractString
```

Inverse une chaîne de caractères. Techniquement, cette fonction inverse les points de code dans une chaîne et son utilité principale est pour le traitement de chaînes en ordre inversé, en particulier pour les recherches d'expressions régulières inversées. Voir aussi [`reverseind`](@ref) pour convertir les indices dans `s` en indices dans `reverse(s)` et vice-versa, et `graphemes` du module `Unicode` pour opérer sur les "caractères" visibles par l'utilisateur (graphemes) plutôt que sur les points de code. Voir aussi [`Iterators.reverse`](@ref) pour une itération en ordre inversé sans faire de copie. Les types de chaînes personnalisés doivent implémenter eux-mêmes la fonction `reverse` et doivent généralement retourner une chaîne du même type et encodage. S'ils retournent une chaîne avec un encodage différent, ils doivent également remplacer `reverseind` pour ce type de chaîne afin de satisfaire `s[reverseind(s,i)] == reverse(s)[i]`.

# Exemples

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! note
    Les exemples ci-dessous peuvent être rendus différemment sur différents systèmes. Les commentaires indiquent comment ils sont censés être rendus


Les caractères combinés peuvent conduire à des résultats surprenants :

```jldoctest
julia> reverse("ax̂e") # le chapeau est au-dessus de x dans l'entrée, au-dessus de e dans la sortie
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # inverse les graphemes ; le chapeau est au-dessus de x dans l'entrée et la sortie
"ex̂a"
```
