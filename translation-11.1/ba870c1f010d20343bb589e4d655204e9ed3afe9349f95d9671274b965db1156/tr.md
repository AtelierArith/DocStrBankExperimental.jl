```
basename(path::AbstractString) -> String
```

Bir yolun dosya adı kısmını alır.

!!! note
    Bu işlev, sonundaki eğik çizgilerin göz ardı edildiği Unix `basename` programından biraz farklıdır; yani `$ basename /foo/bar/` `bar` dönerken, Julia'daki `basename` boş bir dize `""` döner.


# Örnekler

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

Ayrıca bkz. [`dirname`](@ref).
