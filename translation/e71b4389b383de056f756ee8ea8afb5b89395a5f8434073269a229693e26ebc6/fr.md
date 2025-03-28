```
@view A[inds...]
```

Transformez l'expression d'indexation `A[inds...]` en l'appel équivalent [`view`](@ref).

Cela ne peut être appliqué directement qu'à une seule expression d'indexation et est particulièrement utile pour les expressions qui incluent les syntaxes d'indexation spéciales `begin` ou `end` comme `A[begin, 2:end-1]` (car celles-ci ne sont pas prises en charge par la fonction normale [`view`](@ref)).

Notez que `@view` ne peut pas être utilisé comme cible d'une affectation régulière (par exemple, `@view(A[1, 2:end]) = ...`), ni l'affectation indexée non décorée [`A[1, 2:end] = ...`](@ref man-indexed-assignment) ou l'affectation indexée diffusée (`A[1, 2:end] .= ...`) ne ferait une copie. Cependant, cela peut être utile pour *mettre à jour* des affectations diffusées comme `@view(A[1, 2:end]) .+= 1` car c'est une syntaxe simple pour `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1`, et l'expression d'indexation du côté droit ferait autrement une copie sans le `@view`.

Voir aussi [`@views`](@ref) pour passer un bloc entier de code à utiliser des vues pour l'indexation non scalaire.

!!! compat "Julia 1.5"
    Utiliser `begin` dans une expression d'indexation pour se référer au premier index nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```
