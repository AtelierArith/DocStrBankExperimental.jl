```
rank(A::AbstractMatrix; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Real)
```

Calculez le rang numérique d'une matrice en comptant combien de valeurs de sortie de `svdvals(A)` sont supérieures à `max(atol, rtol*σ₁)` où `σ₁` est la plus grande valeur singulière calculée de `A`. `atol` et `rtol` sont respectivement les tolérances absolue et relative. La tolérance relative par défaut est `n*ϵ`, où `n` est la taille de la plus petite dimension de `A`, et `ϵ` est le [`eps`](@ref) du type d'élément de `A`.

!!! note
    Le rang numérique peut être une caractérisation sensible et imprécise des matrices mal conditionnées avec des valeurs singulières proches de la tolérance seuil `max(atol, rtol*σ₁)`. Dans de tels cas, de légères perturbations dans le calcul des valeurs singulières ou dans la matrice peuvent changer le résultat de `rank` en déplaçant une ou plusieurs valeurs singulières au-delà du seuil. Ces variations peuvent même se produire en raison de changements dans les erreurs de flottement entre différentes versions de Julia, architectures, compilateurs ou systèmes d'exploitation.


!!! compat "Julia 1.1"
    Les arguments de mot-clé `atol` et `rtol` nécessitent au moins Julia 1.1. Dans Julia 1.0, `rtol` est disponible en tant qu'argument positionnel, mais cela sera obsolète dans Julia 2.0.


# Exemples

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```
