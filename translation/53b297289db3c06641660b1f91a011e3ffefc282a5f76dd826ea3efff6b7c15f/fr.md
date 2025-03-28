```
Base.rest(collection[, itr_state])
```

Fonction générique pour prendre la queue de `collection`, à partir d'un état d'itération spécifique `itr_state`. Retourne un `Tuple`, si `collection` elle-même est un `Tuple`, un sous-type de `AbstractVector`, si `collection` est un `AbstractArray`, un sous-type de `AbstractString` si `collection` est un `AbstractString`, et un itérateur arbitraire, revenant à `Iterators.rest(collection[, itr_state])`, sinon.

Peut être surchargé pour des types de collection définis par l'utilisateur afin de personnaliser le comportement de [slurping in assignments](@ref destructuring-assignment) en position finale, comme `a, b... = collection`.

!!! compat "Julia 1.6"
    `Base.rest` nécessite au moins Julia 1.6.


Voir aussi : [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref).

# Exemples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
