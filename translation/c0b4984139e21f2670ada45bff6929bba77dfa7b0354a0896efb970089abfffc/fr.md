```
muladd(A, y, z)
```

Multiplication-addition combinée, `A*y .+ z`, pour la multiplication matrice-matrice ou matrice-vecteur. Le résultat est toujours de la même taille que `A*y`, mais `z` peut être plus petit, ou un scalaire.

!!! compat "Julia 1.6"
    Ces méthodes nécessitent Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> A=[1.0 2.0; 3.0 4.0]; B=[1.0 1.0; 1.0 1.0]; z=[0, 100];

julia> muladd(A, B, z)
2×2 Matrix{Float64}:
   3.0    3.0
 107.0  107.0
```
