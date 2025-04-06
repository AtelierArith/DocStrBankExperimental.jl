```
supertypes(T::Type)
```

Renvoie un tuple `(T, ..., Any)` de `T` et de tous ses supertypes, déterminé par des appels successifs à la fonction [`supertype`](@ref), listés dans l'ordre de `<:` et terminés par `Any`.

Voir aussi [`subtypes`](@ref).

# Exemples

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
