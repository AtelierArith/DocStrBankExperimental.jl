```
read(filename::AbstractString)
```

Lire le contenu entier d'un fichier sous forme de `Vector{UInt8}`.

```
read(filename::AbstractString, String)
```

Lire le contenu entier d'un fichier sous forme de chaîne.

```
read(filename::AbstractString, args...)
```

Ouvrir un fichier et lire son contenu. `args` est passé à `read` : cela équivaut à `open(io->read(io, args...), filename)`.
