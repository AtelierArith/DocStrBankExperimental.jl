```
similar(array, [element_type=eltype(array)], [dims=size(array)])
```

Crée un tableau mutable non initialisé avec le type d'élément et la taille donnés, basé sur le tableau source donné. Les deuxième et troisième arguments sont tous deux optionnels, par défaut au `eltype` et à la `size` du tableau donné. Les dimensions peuvent être spécifiées soit comme un seul argument tuple, soit comme une série d'arguments entiers.

Les sous-types d'AbstractArray personnalisés peuvent choisir quel type de tableau spécifique est le mieux adapté à retourner pour le type d'élément et la dimensionnalité donnés. S'ils ne spécialisent pas cette méthode, le défaut est un `Array{element_type}(undef, dims...)`.

Par exemple, `similar(1:10, 1, 4)` retourne un `Array{Int,2}` non initialisé puisque les plages ne sont ni mutables ni supportent 2 dimensions :

```julia-repl
julia> similar(1:10, 1, 4)
1×4 Matrix{Int64}:
 4419743872  4374413872  4419743888  0
```

Inversement, `similar(trues(10,10), 2)` retourne un `BitVector` non initialisé avec deux éléments puisque les `BitArray`s sont à la fois mutables et peuvent supporter des tableaux unidimensionnels :

```julia-repl
julia> similar(trues(10,10), 2)
2-element BitVector:
 0
 0
```

Cependant, puisque les `BitArray`s ne peuvent stocker que des éléments de type [`Bool`](@ref), si vous demandez un type d'élément différent, cela créera un `Array` régulier à la place :

```julia-repl
julia> similar(falses(10), Float64, 2, 4)
2×4 Matrix{Float64}:
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
 2.18425e-314  2.18425e-314  2.18425e-314  2.18425e-314
```

Voir aussi : [`undef`](@ref), [`isassigned`](@ref).
