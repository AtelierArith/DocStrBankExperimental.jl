```
partialsort(v, k, by=identity, lt=isless, rev=false)
```

Variante de [`partialsort!`](@ref) qui copie `v` avant de le trier partiellement, renvoyant ainsi la même chose que `partialsort!` mais laissant `v` non modifié.
