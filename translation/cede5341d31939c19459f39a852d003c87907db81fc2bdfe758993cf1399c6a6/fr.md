```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

Calcule la décomposition en valeurs singulières (SVD) de `A` et renvoie un objet `SVD`.

`U`, `S`, `V` et `Vt` peuvent être obtenus à partir de la factorisation `F` avec `F.U`, `F.S`, `F.V` et `F.Vt`, de sorte que `A = U * Diagonal(S) * Vt`. L'algorithme produit `Vt` et donc `Vt` est plus efficace à extraire que `V`. Les valeurs singulières dans `S` sont triées par ordre décroissant.

L'itération de la décomposition produit les composants `U`, `S` et `V`.

Si `full = false` (par défaut), une SVD "mince" est renvoyée. Pour une matrice `A` de taille $M \times N$, dans la factorisation complète `U` est de taille $M \times M$ et `V` est de taille $N \times N$, tandis que dans la factorisation mince `U` est de taille $M \times K$ et `V` est de taille $N \times K$, où $K = \min(M,N)$ est le nombre de valeurs singulières.

Si `alg = DivideAndConquer()`, un algorithme de diviser pour régner est utilisé pour calculer la SVD. Une autre option (typiquement plus lente mais plus précise) est `alg = QRIteration()`.

!!! compat "Julia 1.3"
    L'argument clé `alg` nécessite Julia 1.3 ou une version ultérieure.


# Exemples

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # Stocker l'objet de factorisation

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # déstructuration via itération

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # Stocker uniquement U

julia> Uonly == U
true
```
