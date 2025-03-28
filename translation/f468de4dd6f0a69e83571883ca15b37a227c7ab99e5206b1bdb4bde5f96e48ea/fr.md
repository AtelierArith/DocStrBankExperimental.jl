```
Threads.Atomic{T}
```

Contient une référence à un objet de type `T`, garantissant qu'il n'est accédé qu'atomiquement, c'est-à-dire de manière sécurisée pour les threads.

Seuls certains types "simples" peuvent être utilisés de manière atomique, à savoir les types primitifs booléen, entier et à virgule flottante. Ceux-ci sont `Bool`, `Int8`...`Int128`, `UInt8`...`UInt128`, et `Float16`...`Float64`.

De nouveaux objets atomiques peuvent être créés à partir de valeurs non atomiques ; si aucune n'est spécifiée, l'objet atomique est initialisé à zéro.

Les objets atomiques peuvent être accédés en utilisant la notation `[]` :

# Exemples

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

Les opérations atomiques utilisent un préfixe `atomic_`, tel que [`atomic_add!`](@ref), [`atomic_xchg!`](@ref), etc.
