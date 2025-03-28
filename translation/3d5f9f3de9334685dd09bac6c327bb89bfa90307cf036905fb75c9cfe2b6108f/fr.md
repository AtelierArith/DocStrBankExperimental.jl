```
BitArray{N} <: AbstractArray{Bool, N}
```

Tableau booléen `N`-dimensionnel économe en espace, utilisant juste un bit pour chaque valeur booléenne.

Les `BitArray` regroupent jusqu'à 64 valeurs dans chaque 8 octets, résultant en une efficacité d'espace de 8x par rapport à `Array{Bool, N}` et permettant à certaines opérations de fonctionner sur 64 valeurs à la fois.

Par défaut, Julia renvoie des `BitArrays` à partir des opérations de [diffusion](@ref Broadcasting) qui génèrent des éléments booléens (y compris les comparaisons avec point comme `.==`) ainsi qu'à partir des fonctions [`trues`](@ref) et [`falses`](@ref).

!!! note
    En raison de son format de stockage compact, l'accès concurrent aux éléments d'un `BitArray` où au moins l'un d'eux est une écriture n'est pas sûr pour les threads.

