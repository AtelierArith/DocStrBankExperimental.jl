```
hypot(x, y)
```

Calculez l'hypoténuse $\sqrt{|x|^2+|y|^2}$ en évitant le débordement et le sous-dépassement.

Ce code est une implémentation de l'algorithme décrit dans : Un algorithme amélioré pour `hypot(a,b)` par Carlos F. Borges. L'article est disponible en ligne sur arXiv à l'adresse   https://arxiv.org/abs/1904.09481

```
hypot(x...)
```

Calculez l'hypoténuse $\sqrt{\sum |x_i|^2}$ en évitant le débordement et le sous-dépassement.

Voir aussi `norm` dans la bibliothèque standard [`LinearAlgebra`](@ref man-linalg).

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2 déborde
ERROR: DomainError with -2.914184810805068e18:
sqrt a été appelé avec un argument réel négatif mais ne renverra qu'un résultat complexe s'il est appelé avec un argument complexe. Essayez sqrt(Complex(x)).
Stacktrace:
[...]

julia> hypot(3, 4im)
5.0

julia> hypot(-5.7)
5.7

julia> hypot(3, 4im, 12.0)
13.0

julia> using LinearAlgebra

julia> norm([a, a, a, a]) == hypot(a, a, a, a)
true
```
