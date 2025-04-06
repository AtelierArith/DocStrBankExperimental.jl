```
hessenberg(A) -> Hessenberg
```

Calculez la décomposition de Hessenberg de `A` et renvoyez un objet `Hessenberg`. Si `F` est l'objet de factorisation, la matrice unitaire peut être accédée avec `F.Q` (de type `LinearAlgebra.HessenbergQ`) et la matrice de Hessenberg avec `F.H` (de type [`UpperHessenberg`](@ref)), l'une ou l'autre pouvant être convertie en une matrice régulière avec `Matrix(F.H)` ou `Matrix(F.Q)`.

Si `A` est [`Hermitienne`](@ref) ou [`Symétrique`](@ref) réelle, alors la décomposition de Hessenberg produit une matrice tridiagonale réelle-symétrique et `F.H` est de type [`SymTridiagonal`](@ref).

Notez que la factorisation décalée `A+μI = Q (H+μI) Q'` peut être construite efficacement par `F + μ*I` en utilisant l'objet [`UniformScaling`](@ref) [`I`](@ref), qui crée un nouvel objet `Hessenberg` avec un stockage partagé et un décalage modifié. Le décalage d'un `F` donné est obtenu par `F.μ`. Cela est utile car plusieurs résolutions décalées `(F + μ*I) \ b` (pour différents `μ` et/ou `b`) peuvent être effectuées efficacement une fois que `F` est créé.

L'itération de la décomposition produit les facteurs `F.Q, F.H, F.μ`.

# Exemples

```julia-repl
julia> A = [4. 9. 7.; 4. 4. 1.; 4. 3. 2.]
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> F = hessenberg(A)
Hessenberg{Float64, UpperHessenberg{Float64, Matrix{Float64}}, Matrix{Float64}, Vector{Float64}, Bool}
Q facteur : 3×3 LinearAlgebra.HessenbergQ{Float64, Matrix{Float64}, Vector{Float64}, false}
H facteur :
3×3 UpperHessenberg{Float64, Matrix{Float64}}:
  4.0      -11.3137       -1.41421
 -5.65685    5.0           2.0
   ⋅        -8.88178e-16   1.0

julia> F.Q * F.H * F.Q'
3×3 Matrix{Float64}:
 4.0  9.0  7.0
 4.0  4.0  1.0
 4.0  3.0  2.0

julia> q, h = F; # déstructuration via itération

julia> q == F.Q && h == F.H
true
```
