```
isabstracttype(T)
```

Déterminez si le type `T` a été déclaré comme un type abstrait (c'est-à-dire en utilisant la syntaxe `abstract type`). Notez que ce n'est pas la négation de `isconcretetype(T)`. Si `T` n'est pas un type, alors renvoyez `false`.

# Exemples

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
