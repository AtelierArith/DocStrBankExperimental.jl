```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

Gibt einen Iterator zurück, der den Verzeichnisbaum eines Verzeichnisses durchläuft. Der Iterator gibt ein Tupel zurück, das `(rootpath, dirs, files)` enthält. Der Verzeichnisbaum kann von oben nach unten oder von unten nach oben durchlaufen werden. Wenn `walkdir` oder `stat` auf einen `IOError` stößt, wird der Fehler standardmäßig erneut ausgelöst. Eine benutzerdefinierte Fehlerbehandlungsfunktion kann über das Schlüsselwortargument `onerror` bereitgestellt werden. `onerror` wird mit einem `IOError` als Argument aufgerufen.

Siehe auch: [`readdir`](@ref).

# Beispiele

```julia
for (root, dirs, files) in walkdir(".")
    println("Verzeichnisse in $root")
    for dir in dirs
        println(joinpath(root, dir)) # Pfad zu Verzeichnissen
    end
    println("Dateien in $root")
    for file in files
        println(joinpath(root, file)) # Pfad zu Dateien
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
