```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

Met à jour la collection avec des paires provenant des autres collections. Les valeurs ayant la même clé seront combinées à l'aide de la fonction de combinaison. La forme curryée `mergewith!(combine)` renvoie la fonction `(args...) -> mergewith!(combine, args...)`.

La méthode `merge!(combine::Union{Function,Type}, args...)` en tant qu'alias de `mergewith!(combine, args...)` est toujours disponible pour la compatibilité ascendante.

!!! compat "Julia 1.5"
    `mergewith!` nécessite Julia 1.5 ou une version ultérieure.


# Exemples

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 0
  1 => 4
```
