```
kron(A, B)
```

Calcule le produit de Kronecker de deux vecteurs, matrices ou nombres.

Pour les vecteurs réels `v` et `w`, le produit de Kronecker est lié au produit extérieur par `kron(v,w) == vec(w * transpose(v))` ou `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))`. Notez comment l'ordre de `v` et `w` diffère à gauche et à droite de ces expressions (en raison du stockage en colonne). Pour les vecteurs complexes, le produit extérieur `w * v'` diffère également par la conjugaison de `v`.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
