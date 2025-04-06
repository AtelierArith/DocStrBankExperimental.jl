```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

Calcule la décomposition en valeurs propres de `A`, retournant un objet de factorisation [`Eigen`](@ref) `F` qui contient les valeurs propres dans `F.values` et les vecteurs propres dans les colonnes de la matrice `F.vectors`. Cela correspond à la résolution d'un problème de valeurs propres de la forme `Ax =  λx`, où `A` est une matrice, `x` est un vecteur propre, et `λ` est une valeur propre. (Le `k`-ième vecteur propre peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

Les fonctions suivantes sont disponibles pour les objets `Eigen` : [`inv`](@ref), [`det`](@ref), et [`isposdef`](@ref).

Pour les matrices générales non symétriques, il est possible de spécifier comment la matrice est équilibrée avant le calcul des vecteurs propres. L'option `permute=true` permute la matrice pour la rapprocher d'une forme triangulaire supérieure, et `scale=true` met à l'échelle la matrice par ses éléments diagonaux pour rendre les lignes et les colonnes plus égales en norme. La valeur par défaut est `true` pour les deux options.

Par défaut, les valeurs et vecteurs propres sont triés lexicographiquement par `(real(λ),imag(λ))`. Une fonction de comparaison différente `by(λ)` peut être passée à `sortby`, ou vous pouvez passer `sortby=nothing` pour laisser les valeurs propres dans un ordre arbitraire. Certains types de matrices spéciaux (par exemple [`Diagonal`](@ref) ou [`SymTridiagonal`](@ref)) peuvent implémenter leur propre convention de tri et ne pas accepter un mot-clé `sortby`.

# Exemples

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuration via itération

julia> vals == F.values && vecs == F.vectors
true
```
