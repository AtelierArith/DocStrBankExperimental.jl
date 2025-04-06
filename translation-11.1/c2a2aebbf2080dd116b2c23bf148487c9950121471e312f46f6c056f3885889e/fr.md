```
Time(t::AbstractString, format::AbstractString; locale="english") -> Time
```

Construit un `Time` en analysant la chaîne de temps `t` suivant le modèle donné dans la chaîne `format` (voir [`DateFormat`](@ref) pour la syntaxe).

!!! note
    Cette méthode crée un objet `DateFormat` chaque fois qu'elle est appelée. Il est recommandé de créer un objet [`DateFormat`](@ref) à la place et de l'utiliser comme deuxième argument pour éviter une perte de performance lors de l'utilisation du même format de manière répétée.


# Exemples

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # préféré
2-element Vector{Time}:
 12:34:00
 02:34:00
```
