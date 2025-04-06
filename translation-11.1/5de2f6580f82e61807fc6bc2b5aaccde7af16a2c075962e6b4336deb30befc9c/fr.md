```
pathof(m::Module)
```

Retourne le chemin du fichier `m.jl` qui a été utilisé pour `importer` le module `m`, ou `nothing` si `m` n'a pas été importé d'un package.

Utilisez [`dirname`](@ref) pour obtenir la partie répertoire et [`basename`](@ref) pour obtenir la partie nom de fichier du chemin.

Voir aussi [`pkgdir`](@ref).
