```
DateTime(dt::AbstractString, format::AbstractString; locale="english") -> DateTime
```

Construit un `DateTime` en analysant la chaîne de date et heure `dt` suivant le modèle donné dans la chaîne `format` (voir [`DateFormat`](@ref) pour la syntaxe).

!!! note
    Cette méthode crée un objet `DateFormat` chaque fois qu'elle est appelée. Il est recommandé de créer un objet [`DateFormat`](@ref) à la place et de l'utiliser comme deuxième argument pour éviter une perte de performance lors de l'utilisation du même format de manière répétée.


# Exemples

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # préféré
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
