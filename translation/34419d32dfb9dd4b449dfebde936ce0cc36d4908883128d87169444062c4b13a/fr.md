```
qr(A, pivot = NoPivot(); blocksize) -> F
```

Calcule la factorisation QR de la matrice `A` : une matrice orthogonale (ou unitaire si `A` est à valeurs complexes) `Q`, et une matrice triangulaire supérieure `R` telle que

$$
A = Q R
$$

L'objet retourné `F` stocke la factorisation dans un format compact :

  * si `pivot == ColumnNorm()` alors `F` est un objet [`QRPivoted`](@ref),
  * sinon, si le type d'élément de `A` est un type BLAS ([`Float32`](@ref), [`Float64`](@ref), `ComplexF32` ou `ComplexF64`), alors `F` est un objet [`QRCompactWY`](@ref),
  * sinon `F` est un objet [`QR`](@ref).

Les composants individuels de la décomposition `F` peuvent être récupérés via des accesseurs de propriété :

  * `F.Q` : la matrice orthogonale/unitaire `Q`
  * `F.R` : la matrice triangulaire supérieure `R`
  * `F.p` : le vecteur de permutation du pivot ([`QRPivoted`](@ref) uniquement)
  * `F.P` : la matrice de permutation du pivot ([`QRPivoted`](@ref) uniquement)

!!! note
    Chaque référence au facteur triangulaire supérieur via `F.R` alloue un nouveau tableau. Il est donc conseillé de mettre en cache ce tableau, par exemple, en `R = F.R` et de continuer à travailler avec `R`.


L'itération de la décomposition produit les composants `Q`, `R`, et si présent `p`.

Les fonctions suivantes sont disponibles pour les objets `QR` : [`inv`](@ref), [`size`](@ref), et [`\`](@ref). Lorsque `A` est rectangulaire, `\` renverra une solution des moindres carrés et si la solution n'est pas unique, celle avec la plus petite norme est retournée. Lorsque `A` n'est pas de rang complet, une factorisation avec (colonne) pivot est requise pour obtenir une solution de norme minimale.

La multiplication par rapport à `Q` complet/carré ou non complet/carré est autorisée, c'est-à-dire que `F.Q*F.R` et `F.Q*A` sont pris en charge. Une matrice `Q` peut être convertie en une matrice régulière avec [`Matrix`](@ref). Cette opération renvoie le facteur Q "mince", c'est-à-dire que si `A` est `m`×`n` avec `m>=n`, alors `Matrix(F.Q)` produit une matrice `m`×`n` avec des colonnes orthonormales. Pour récupérer le facteur Q "complet", une matrice orthogonale `m`×`m`, utilisez `F.Q*I` ou `collect(F.Q)`. Si `m<=n`, alors `Matrix(F.Q)` produit une matrice orthogonale `m`×`m`.

La taille de bloc pour la décomposition QR peut être spécifiée par l'argument clé `blocksize :: Integer` lorsque `pivot == NoPivot()` et `A isa StridedMatrix{<:BlasFloat}`. Elle est ignorée lorsque `blocksize > minimum(size(A))`. Voir [`QRCompactWY`](@ref).

!!! compat "Julia 1.4"
    L'argument clé `blocksize` nécessite Julia 1.4 ou une version ultérieure.


# Exemples

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Facteur Q : 3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
Facteur R :
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! note
    `qr` renvoie plusieurs types car LAPACK utilise plusieurs représentations qui minimisent les besoins de stockage mémoire des produits de réflecteurs élémentaires de Householder, de sorte que les matrices `Q` et `R` peuvent être stockées de manière compacte plutôt que comme deux matrices denses séparées.

