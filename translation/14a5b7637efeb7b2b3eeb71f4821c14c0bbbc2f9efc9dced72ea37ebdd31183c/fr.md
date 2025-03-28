```
touch(path::AbstractString)
touch(fd::File)
```

Met à jour l'horodatage de dernière modification d'un fichier à l'heure actuelle.

Si le fichier n'existe pas, un nouveau fichier est créé.

Retourne `path`.

# Exemples

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

Nous pouvons voir que [`mtime`](@ref) a été modifié par `touch`.
