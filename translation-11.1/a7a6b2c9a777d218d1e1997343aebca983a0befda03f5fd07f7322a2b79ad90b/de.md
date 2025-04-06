```
pkgdir(m::Module[, paths::String...])
```

Gibt das Stammverzeichnis des Pakets zurück, das das Modul `m` deklariert hat, oder `nothing`, wenn `m` nicht in einem Paket deklariert wurde. Optional können weitere Pfadkomponenten-Strings bereitgestellt werden, um einen Pfad innerhalb des Paketstamms zu erstellen.

Um das Stammverzeichnis des Pakets zu erhalten, das das aktuelle Modul implementiert, kann die Form `pkgdir(@__MODULE__)` verwendet werden.

Wenn ein Erweiterungsmodul angegeben ist, wird das Stammverzeichnis des übergeordneten Pakets zurückgegeben.

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

Siehe auch [`pathof`](@ref).

!!! compat "Julia 1.7"
    Das optionale Argument `paths` erfordert mindestens Julia 1.7.

