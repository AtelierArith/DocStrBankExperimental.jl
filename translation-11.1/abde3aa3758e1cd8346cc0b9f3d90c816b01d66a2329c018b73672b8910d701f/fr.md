```
lu(A::AbstractSparseMatrixCSC; check = true, q = nothing, control = get_umfpack_control()) -> F::UmfpackLU
```

Calculez la factorisation LU d'une matrice creuse `A`.

Pour une matrice creuse `A` avec un type d'élément réel ou complexe, le type de retour de `F` est `UmfpackLU{Tv, Ti}`, avec `Tv` = [`Float64`](@ref) ou `ComplexF64` respectivement et `Ti` est un type entier ([`Int32`](@ref) ou [`Int64`](@ref)).

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

Le permutation `q` peut être soit un vecteur de permutation soit `nothing`. Si aucun vecteur de permutation n'est fourni ou si `q` est `nothing`, le défaut d'UMFPACK est utilisé. Si la permutation n'est pas basée sur zéro, une copie basée sur zéro est faite.

Le vecteur `control` par défaut correspond à la configuration par défaut du package Julia SparseArrays pour UMFPACK (NB : cela est modifié par rapport aux défauts d'UMFPACK pour désactiver le raffinement itératif), mais peut être changé en passant un vecteur de longueur `UMFPACK_CONTROL`, voir le manuel d'UMFPACK pour les configurations possibles. Par exemple, pour réactiver le raffinement itératif :

```
umfpack_control = SparseArrays.UMFPACK.get_umfpack_control(Float64, Int64) # lire la configuration par défaut de Julia pour une matrice creuse Float64
SparseArrays.UMFPACK.show_umf_ctrl(umfpack_control) # optionnel - afficher les valeurs
umfpack_control[SparseArrays.UMFPACK.JL_UMFPACK_IRSTEP] = 2.0 # réactiver le raffinement itératif (2 est le maximum par défaut d'UMFPACK)

Alu = lu(A; control = umfpack_control)
x = Alu \ b   # résoudre Ax = b, y compris le raffinement itératif d'UMFPACK
```

Les composants individuels de la factorisation `F` peuvent être accessibles par indexation :

| Composant | Description                                  |
|:--------- |:-------------------------------------------- |
| `L`       | partie `L` (triangulaire inférieure) de `LU` |
| `U`       | partie `U` (triangulaire supérieure) de `LU` |
| `p`       | permutation à droite `Vector`                |
| `q`       | permutation à gauche `Vector`                |
| `Rs`      | `Vector` de facteurs d'échelle               |
| `:`       | composants `(L,U,p,q,Rs)`                    |

La relation entre `F` et `A` est

`F.L*F.U == (F.Rs .* A)[F.p, F.q]`

`F` prend également en charge les fonctions suivantes :

  * [`\`](@ref)
  * [`det`](@ref)

Voir aussi [`lu!`](@ref)

!!! note
    `lu(A::AbstractSparseMatrixCSC)` utilise la bibliothèque UMFPACK[^ACM832] qui fait partie de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). Comme cette bibliothèque ne prend en charge que les matrices creuses avec des éléments [`Float64`](@ref) ou `ComplexF64`, `lu` convertit `A` en une copie de type `SparseMatrixCSC{Float64}` ou `SparseMatrixCSC{ComplexF64}` selon le cas.


[^ACM832]: Davis, Timothy A. (2004b). Algorithm 832: UMFPACK V4.3–-an Unsymmetric-Pattern Multifrontal Method. ACM Trans. Math. Softw., 30(2), 196–199. [doi:10.1145/992200.992206](https://doi.org/10.1145/992200.992206)
