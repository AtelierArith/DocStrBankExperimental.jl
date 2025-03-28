```
ncodeunits(s::AbstractString) -> Int
```

Retourne le nombre d'unités de code dans une chaîne. Les indices qui sont dans les limites pour accéder à cette chaîne doivent satisfaire `1 ≤ i ≤ ncodeunits(s)`. Tous ces indices ne sont pas valides – ils peuvent ne pas être le début d'un caractère, mais ils retourneront une valeur d'unité de code lors de l'appel de `codeunit(s,i)`.

# Exemples

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

Voir aussi [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref).
