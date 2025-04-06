```
svd(A, B) -> GeneralizedSVD
```

Calculez le SVD généralisé de `A` et `B`, retournant un objet de factorisation `GeneralizedSVD` `F` tel que `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`

  * `U` est une matrice orthogonale de M par M,
  * `V` est une matrice orthogonale de P par P,
  * `Q` est une matrice orthogonale de N par N,
  * `D1` est une matrice diagonale de M par (K+L) avec des 1 dans les K premières entrées,
  * `D2` est une matrice de P par (K+L) dont le bloc supérieur droit de L par L est diagonal,
  * `R0` est une matrice de (K+L) par N dont le bloc supérieur droit de (K+L) par (K+L) est non singulier et triangulaire supérieur,

`K+L` est le rang numérique effectif de la matrice `[A; B]`.

L'itération de la décomposition produit les composants `U`, `V`, `Q`, `D1`, `D2`, et `R0`.

Le SVD généralisé est utilisé dans des applications telles que lorsque l'on veut comparer combien appartient à `A` par rapport à combien appartient à `B`, comme dans le génome humain contre le génome de la levure, ou le signal contre le bruit, ou entre les clusters contre à l'intérieur des clusters. (Voir Edelman et Wang pour discussion : https://arxiv.org/abs/1901.00485)

Il décompose `[A; B]` en `[UC; VS]H`, où `[UC; VS]` est une base orthogonale naturelle pour l'espace des colonnes de `[A; B]`, et `H = RQ'` est une base non orthogonale naturelle pour l'espace des lignes de `[A;B]`, où les lignes supérieures sont le plus étroitement attribuées à la matrice `A`, et les lignes inférieures à la matrice `B`. Les matrices multi-cosinus/sinus `C` et `S` fournissent une mesure multiple de combien `A` contre combien `B`, et `U` et `V` fournissent des directions dans lesquelles ces mesures sont effectuées.

# Exemples

```jldoctest
julia> A = randn(3,2); B=randn(4,2);

julia> F = svd(A, B);

julia> U,V,Q,C,S,R = F;

julia> H = R*Q';

julia> [A; B] ≈ [U*C; V*S]*H
true

julia> [A; B] ≈ [F.U*F.D1; F.V*F.D2]*F.R0*F.Q'
true

julia> Uonly, = svd(A,B);

julia> U == Uonly
true
```
