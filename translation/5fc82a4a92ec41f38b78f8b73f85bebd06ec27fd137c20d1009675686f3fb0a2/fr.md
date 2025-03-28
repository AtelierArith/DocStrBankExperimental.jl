```
eltype(type)
```

Détermine le type des éléments générés en itérant une collection du `type` donné. Pour les types de dictionnaires, cela sera un `Pair{KeyType,ValType}`. La définition `eltype(x) = eltype(typeof(x))` est fournie pour la commodité afin que des instances puissent être passées au lieu de types. Cependant, la forme qui accepte un argument de type doit être définie pour les nouveaux types.

Voir aussi : [`keytype`](@ref), [`typeof`](@ref).

# Exemples

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
