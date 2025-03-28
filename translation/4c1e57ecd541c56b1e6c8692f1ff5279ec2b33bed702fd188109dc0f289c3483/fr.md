```
cumsum(A; dims::Integer)
```

Somme cumulative le long de la dimension `dims`. Voir aussi [`cumsum!`](@ref) pour utiliser un tableau de sortie préalloué, à la fois pour des performances et pour contrôler la précision de la sortie (par exemple, pour éviter le débordement).

# Exemples

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! note
    Le `eltype` du tableau de retour est `Int` pour les entiers signés de moins de la taille d'un mot système et `UInt` pour les entiers non signés de moins de la taille d'un mot système. Pour préserver le `eltype` des tableaux avec de petits entiers signés ou non signés, `accumulate(+, A)` devrait être utilisé.

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    Dans le premier cas, les entiers sont élargis à la taille d'un mot système et donc le résultat est `Int64[100, 128]`. Dans le second cas, aucun élargissement n'a lieu et le débordement d'entier résulte en `Int8[100, -128]`.

