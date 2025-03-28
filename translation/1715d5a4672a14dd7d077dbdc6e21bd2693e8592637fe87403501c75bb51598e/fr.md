```
Date(d::AbstractString, format::AbstractString; locale="english") -> Date
```

Construit un `Date` en analysant la chaîne de date `d` suivant le modèle donné dans la chaîne `format` (voir [`DateFormat`](@ref) pour la syntaxe).

!!! note
    Cette méthode crée un objet `DateFormat` chaque fois qu'elle est appelée. Il est recommandé de créer un objet [`DateFormat`](@ref) à la place et de l'utiliser comme deuxième argument pour éviter une perte de performance lors de l'utilisation du même format de manière répétée.


# Exemples

```jldoctest
julia> Date("2020-01-01", "yyyy-mm-dd")
2020-01-01

julia> a = ("2020-01-01", "2020-01-02");

julia> [Date(d, dateformat"yyyy-mm-dd") for d ∈ a] # préféré
2-element Vector{Date}:
 2020-01-01
 2020-01-02
```
