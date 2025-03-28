```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

Parent et conducteur expert pour [`sparse`](@ref); voir [`sparse`](@ref) pour une utilisation de base. Cette méthode permet à l'utilisateur de fournir un stockage préalloué pour les objets intermédiaires de `sparse` et le résultat comme décrit ci-dessous. Cette capacité permet une construction successive plus efficace de [`SparseMatrixCSC`](@ref)s à partir de représentations coordonnées, et permet également l'extraction d'une représentation de colonne non triée de la transposée du résultat sans coût supplémentaire.

Cette méthode se compose de trois étapes majeures : (1) Tri par comptage de la représentation coordonnée fournie en une forme CSR de ligne non triée incluant des entrées répétées. (2) Balayage à travers la forme CSR, calculant simultanément le tableau des pointeurs de colonne de la forme CSC désirée, détectant les entrées répétées et reconditionnant la forme CSR avec les entrées répétées combinées ; cette étape produit une forme CSR de ligne non triée sans entrées répétées. (3) Tri par comptage de la forme CSR précédente en une forme CSC entièrement triée sans entrées répétées.

Les tableaux d'entrée `csrrowptr`, `csrcolval` et `csrnzval` constituent le stockage pour les formes CSR intermédiaires et nécessitent `length(csrrowptr) >= m + 1`, `length(csrcolval) >= length(I)`, et `length(csrnzval >= length(I))`. Le tableau d'entrée `klasttouch`, espace de travail pour la deuxième étape, nécessite `length(klasttouch) >= n`. Les tableaux d'entrée optionnels `csccolptr`, `cscrowval` et `cscnzval` constituent le stockage pour la forme CSC retournée `S`. Si nécessaire, ceux-ci sont redimensionnés automatiquement pour satisfaire `length(csccolptr) = n + 1`, `length(cscrowval) = nnz(S)` et `length(cscnzval) = nnz(S)` ; par conséquent, si `nnz(S)` est inconnu au départ, il suffit de passer des vecteurs vides du type approprié (`Vector{Ti}()` et `Vector{Tv}()` respectivement), ou d'appeler la méthode `sparse!` en négligeant `cscrowval` et `cscnzval`.

Au retour, `csrrowptr`, `csrcolval` et `csrnzval` contiennent une représentation de colonne non triée de la transposée du résultat.

Vous pouvez réutiliser le stockage des tableaux d'entrée (`I`, `J`, `V`) pour les tableaux de sortie (`csccolptr`, `cscrowval`, `cscnzval`). Par exemple, vous pouvez appeler `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)`. Notez qu'ils seront redimensionnés pour satisfaire les conditions ci-dessus.

Pour des raisons d'efficacité, cette méthode ne vérifie pas les arguments au-delà de `1 <= I[k] <= m` et `1 <= J[k] <= n`. Utilisez avec précaution. Tester avec `--check-bounds=yes` est judicieux.

Cette méthode s'exécute en temps `O(m, n, length(I))`. L'algorithme HALFPERM décrit dans F. Gustavson, "Deux algorithmes rapides pour les matrices creuses : multiplication et transposition permutée," ACM TOMS 4(3), 250-269 (1978) a inspiré l'utilisation par cette méthode d'une paire de tris par comptage.
