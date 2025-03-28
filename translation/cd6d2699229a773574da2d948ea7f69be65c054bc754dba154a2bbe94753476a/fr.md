```
schur(A) -> F::Schur
```

Calcule la factorisation de Schur de la matrice `A`. Le facteur de Schur (quasi) triangulaire peut être obtenu à partir de l'objet `Schur` `F` avec soit `F.Schur` soit `F.T` et les vecteurs de Schur orthogonaux/unitaires peuvent être obtenus avec `F.vectors` ou `F.Z` de sorte que `A = F.vectors * F.Schur * F.vectors'`. Les valeurs propres de `A` peuvent être obtenues avec `F.values`.

Pour un `A` réel, la factorisation de Schur est "quasitriangulaire", ce qui signifie qu'elle est supérieurement triangulaire sauf avec des blocs diagonaux de 2×2 pour toute paire conjuguée de valeurs propres complexes ; cela permet à la factorisation d'être purement réelle même lorsqu'il y a des valeurs propres complexes. Pour obtenir la factorisation de Schur (complexe) purement supérieurement triangulaire à partir d'une factorisation quasitriangulaire réelle, vous pouvez utiliser `Schur{Complex}(schur(A))`.

L'itération de la décomposition produit les composants `F.T`, `F.Z` et `F.values`.

# Exemples

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T factor:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z factor:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
valeurs propres:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # déstructuration via itération

julia> t == F.T && z == F.Z && vals == F.values
true
```
