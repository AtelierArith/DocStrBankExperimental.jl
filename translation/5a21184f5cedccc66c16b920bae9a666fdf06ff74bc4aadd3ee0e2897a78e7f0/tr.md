```
isfile(path) -> Bool
```

`path` bir normal dosya ise `true`, aksi takdirde `false` döner.

# Örnekler

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

Ayrıca [`isdir`](@ref) ve [`ispath`](@ref) bakınız.
