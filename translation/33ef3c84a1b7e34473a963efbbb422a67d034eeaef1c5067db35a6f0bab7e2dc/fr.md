```
cat(A...; dims)
```

Concaténer les tableaux d'entrée le long des dimensions spécifiées dans `dims`.

Le long d'une dimension `d in dims`, la taille du tableau de sortie est `sum(size(a,d) for a in A)`. Le long des autres dimensions, tous les tableaux d'entrée doivent avoir la même taille, qui sera également la taille du tableau de sortie le long de ces dimensions.

Si `dims` est un seul nombre, les différents tableaux sont étroitement regroupés le long de cette dimension. Si `dims` est un itérable contenant plusieurs dimensions, les positions le long de ces dimensions sont augmentées simultanément pour chaque tableau d'entrée, remplissant de zéros ailleurs. Cela permet de construire des matrices diagonales par blocs comme `cat(matrices...; dims=(1,2))`, et leurs analogues de dimensions supérieures.

Le cas particulier `dims=1` est [`vcat`](@ref), et `dims=2` est [`hcat`](@ref). Voir aussi [`hvcat`](@ref), [`hvncat`](@ref), [`stack`](@ref), [`repeat`](@ref).

Le mot-clé accepte également `Val(dims)`.

!!! compat "Julia 1.8"
    Pour plusieurs dimensions `dims = Val(::Tuple)` a été ajouté dans Julia 1.8.


# Exemples

Concaténer deux tableaux dans différentes dimensions :

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# Aide Étendue

Concaténer des tableaux 3D :

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

Concaténer des tableaux de tailles différentes :

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # même que hcat
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

Construire une matrice diagonale par blocs :

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # diagonale par blocs
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat` ne joint pas deux chaînes, vous voudrez peut-être utiliser `*`.


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
