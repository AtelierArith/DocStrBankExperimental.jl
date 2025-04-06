```
Set{T} <: AbstractSet{T}
```

Les `Set` sont des conteneurs mutables qui fournissent des tests d'appartenance rapides.

Les `Set` ont des implémentations efficaces des opérations sur les ensembles telles que `in`, `union` et `intersect`. Les éléments d'un `Set` sont uniques, comme déterminé par la définition de `isequal` des éléments. L'ordre des éléments dans un `Set` est un détail d'implémentation et ne peut pas être pris en compte.

Voir aussi : [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# Exemples

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} avec 3 éléments :
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} avec 4 éléments :
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) est faux
false

julia> NaN in s # isequal(NaN, NaN) est vrai
true
```
