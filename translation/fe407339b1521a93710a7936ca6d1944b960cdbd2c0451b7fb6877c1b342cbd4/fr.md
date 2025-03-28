```
isdir(path) -> Bool
```

Retourne `true` si `path` est un répertoire, `false` sinon.

# Exemples

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

Voir aussi [`isfile`](@ref) et [`ispath`](@ref).
