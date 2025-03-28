```
pkgversion(m::Module)
```

Renvoie la version du package qui a importé le module `m`, ou `nothing` si `m` n'a pas été importé d'un package, ou importé d'un package sans champ de version défini.

La version est lue à partir du Project.toml du package lors du chargement du package.

Pour obtenir la version du package qui a importé le module actuel, la forme `pkgversion(@__MODULE__)` peut être utilisée.

!!! compat "Julia 1.9"
    Cette fonction a été introduite dans Julia 1.9.

