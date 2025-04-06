```
hash(x[, h::UInt]) -> UInt
```

Calculez un code de hachage entier tel que `isequal(x,y)` implique `hash(x)==hash(y)`. L'argument optionnel `h` est un autre code de hachage à mélanger avec le résultat.

Les nouveaux types doivent implémenter la forme à 2 arguments, généralement en appelant de manière récursive la méthode `hash` à 2 arguments afin de mélanger les hachages des contenus entre eux (et avec `h`). En général, tout type qui implémente `hash` doit également implémenter son propre [`==`](@ref) (d'où [`isequal`](@ref)) pour garantir la propriété mentionnée ci-dessus.

La valeur de hachage peut changer lorsqu'un nouveau processus Julia est démarré.

```jldoctest
julia> a = hash(10)
0x95ea2955abd45275

julia> hash(10, a) # n'utilisez que la sortie d'une autre fonction de hachage comme deuxième argument
0xd42bad54a8575b16
```

Voir aussi : [`objectid`](@ref), [`Dict`](@ref), [`Set`](@ref).
