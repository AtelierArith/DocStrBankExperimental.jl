```
isfile(path) -> Bool
```

Retourne `true` si `path` est un fichier régulier, `false` sinon.

# Exemples

```jldoctest
julia> isfile(homedir())
false

julia> filename = "test_file.txt";

julia> write(filename, "Hello world!");

julia> isfile(filename)
true

julia> rm(filename);

julia> isfile(filename)
false
```

Voir aussi [`isdir`](@ref) et [`ispath`](@ref).
