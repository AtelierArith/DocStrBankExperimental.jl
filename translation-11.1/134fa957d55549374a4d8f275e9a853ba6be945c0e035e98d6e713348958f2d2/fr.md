```
RegexMatch <: AbstractMatch
```

Un type représentant une seule correspondance à un [`Regex`](@ref) trouvée dans une chaîne. Typiquement créé à partir de la fonction [`match`](@ref).

Le champ `match` stocke la sous-chaîne de la chaîne entière correspondante. Le champ `captures` stocke les sous-chaînes pour chaque groupe de capture, indexées par numéro. Pour indexer par nom de groupe de capture, l'objet de correspondance entier doit être indexé à la place, comme montré dans les exemples. La localisation du début de la correspondance est stockée dans le champ `offset`. Le champ `offsets` stocke les emplacements du début de chaque groupe de capture, avec 0 désignant un groupe qui n'a pas été capturé.

Ce type peut être utilisé comme un itérateur sur les groupes de capture du `Regex`, produisant les sous-chaînes capturées dans chaque groupe. En raison de cela, les captures d'une correspondance peuvent être déstructurées. Si un groupe n'a pas été capturé, `nothing` sera produit à la place d'une sous-chaîne.

Des méthodes qui acceptent un objet `RegexMatch` sont définies pour [`iterate`](@ref), [`length`](@ref), [`eltype`](@ref), [`keys`](@ref keys(::RegexMatch)), [`haskey`](@ref), et [`getindex`](@ref), où les clés sont les noms ou numéros d'un groupe de capture. Voir [`keys`](@ref keys(::RegexMatch)) pour plus d'informations.

# Exemples

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # déstructurer les groupes de capture par itération

julia> hr
"11"
```
