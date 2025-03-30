```
isdir(path) -> Bool
```

`path` bir dizin ise `true`, aksi takdirde `false` döner.

# Örnekler

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

Ayrıca [`isfile`](@ref) ve [`ispath`](@ref) bakınız.
