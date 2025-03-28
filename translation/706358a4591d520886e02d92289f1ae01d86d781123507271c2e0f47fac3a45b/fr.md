```
sqrt(A::AbstractMatrix)
```

Si `A` n'a pas d'autovalues réelles négatives, calculez la racine carrée principale de la matrice `A`, c'est-à-dire la matrice unique $X$ dont les autovalues ont une partie réelle positive telle que $X^2 = A$. Sinon, une racine carrée non principale est retournée.

Si `A` est réelle-symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer la racine carrée. Pour de telles matrices, les autovalues λ qui semblent légèrement négatives en raison d'erreurs d'arrondi sont traitées comme si elles étaient nulles. Plus précisément, les matrices avec toutes les autovalues `≥ -rtol*(max |λ|)` sont considérées comme semi-définies (produisant une racine carrée hermitienne), avec les autovalues négatives considérées comme nulles. `rtol` est un argument clé pour `sqrt` (dans le cas hermitien/réel-symétrique uniquement) qui par défaut est la précision machine multipliée par `size(A,1)`.

Sinon, la racine carrée est déterminée par la méthode de Björck-Hammarling [^BH83], qui calcule la forme de Schur complexe ([`schur`](@ref)) puis la racine carrée complexe du facteur triangulaire. Si une racine carrée réelle existe, alors une extension de cette méthode [^H87] qui calcule la forme de Schur réelle puis la racine carrée réelle du facteur quasi-triangulaire est utilisée à la place.

[^BH83]: Åke Björck et Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# Exemples

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
