```
partialsort(v, k, by=identity, lt=isless, rev=false)
```

Variante von [`partialsort!`](@ref), die `v` kopiert, bevor sie es teilweise sortiert, und somit dasselbe zurückgibt wie `partialsort!`, aber `v` unverändert lässt.
