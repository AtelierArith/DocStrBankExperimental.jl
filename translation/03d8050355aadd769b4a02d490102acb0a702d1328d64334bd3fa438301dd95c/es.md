```
partialsort(v, k, by=identity, lt=isless, rev=false)
```

Variante de [`partialsort!`](@ref) que copia `v` antes de ordenarlo parcialmente, devolviendo así lo mismo que `partialsort!` pero dejando `v` sin modificar.
