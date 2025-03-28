Lockable(value, lock = ReentrantLock())

Crée un objet `Lockable` qui enveloppe `value` et l'associe au `lock` fourni. Cet objet prend en charge [`@lock`](@ref), [`lock`](@ref), [`trylock`](@ref), [`unlock`](@ref). Pour accéder à la valeur, indexez l'objet verrouillable tout en maintenant le verrou.

!!! compat "Julia 1.11"
    Nécessite au moins Julia 1.11.


## Exemple

```jldoctest
julia> locked_list = Base.Lockable(Int[]);

julia> @lock(locked_list, push!(locked_list[], 1)) # doit maintenir le verrou pour accéder à la valeur
1-element Vector{Int64}:
 1

julia> lock(summary, locked_list)
"1-element Vector{Int64}"
```
